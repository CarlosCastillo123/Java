# Final Project
## Code
### Part one that loads the data from text file into the data base
Code used to execute the sql table is included in the commented section
``` java
import java.io.FileNotFoundException;
import java.sql.*;
import java.awt.GridBagConstraints;
import java.awt.GridBagLayout;
import java.awt.Insets;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JSpinner;
import javax.swing.JTextField;
import javax.swing.SpinnerNumberModel;
import javax.swing.event.ChangeEvent;
import javax.swing.event.ChangeListener;


// Create a database in mySQL called 'auto'
/*    1. mpg:           continuous
    2. cylinders:     multi-valued discrete
    3. displacement:  continuous
    4. horsepower:    continuous
    5. weight:        continuous
    6. acceleration:  continuous
    7. model year:    multi-valued discrete
    8. origin:        multi-valued discrete
    9. car name:      string (unique for each instance)
>    create table Car (
                                         mpg DECIMAL(5,2),
                                          cylinders INT,
                                         displacement DECIMAL(5,2),
                                          horsepower DECIMAL(5,2),
                                          weight DECIMAL(6,2),
                                          acceleration DECIMAL(5,2),
                                          modelYear INT,
                                          origin INT,
                                          carName varchar(50)
                                          );

 */

public class DbProject {

    public static void main(String[] args)
            throws SQLException, ClassNotFoundException, FileNotFoundException {
        // Parse data to insert into file;
        // Load the JDBC driver
        Class.forName("com.mysql.cj.jdbc.Driver");
        System.out.println("Driver loaded");
        // Parse data to insert into file;


        // Establish a connection
        // Assuming the database name is 'testdb', user is 'testuser'
        // and password is 'Pa$$word'
        Connection connection = DriverManager.getConnection
                ("jdbc:mysql://localhost/auto", "testuser", "Pa$$word");
        System.out.println("Database connected");

        // Create a statement
        //Statement statement = connection.createStatement();
      /*  File autoData = new File("autoData.txt");
        try (Scanner fileReader = new Scanner(autoData)) {
            while (
            fileReader.hasNextLine()) {
                ;

                String dataMPG = (fileReader.next());

                int dataCy = Integer.parseInt(fileReader.next().replace(".", ""));
                double dataDis = Double.parseDouble(fileReader.next());
                double dataHp = Double.parseDouble(fileReader.next());
                double dataW = Double.parseDouble(fileReader.next());
                double dataA = Double.parseDouble(fileReader.next());
                int dataY = Integer.parseInt(fileReader.next().replace(".", ""));
                int dataO = Integer.parseInt(fileReader.next().replace(".", ""));
                String dataCn = fileReader.nextLine();

                // String sql = String.format("INSERT INTO Car values( '%s','%s','%s','%s','%s','%s','%s','%s','%s')", iDataMpg
                //        , dataCy, dataDis, dataHp, dataW, dataA, dataY, dataO, dataCn);
                // System.out.println(sql);
                Statement statement = connection.createStatement();
                //ResultSet resultSet = statement.executeQuery(sql);
                // int executeUpdate = statement.executeUpdate
                //("insert into Car ()")
                String sql = "INSERT INTO Car (mpg, cylinders, displacement, horsepower, weight, acceleration, modelYear, origin, carName)" +
                        "values(?,?,?,?,?,?,?,?,?)";
                try {
                    PreparedStatement pstmt = connection.prepareStatement(sql);
                    pstmt.setDouble(1, Double.parseDouble(dataMPG));
                    pstmt.setInt(2, dataCy);
                    pstmt.setDouble(3, dataDis);
                    pstmt.setDouble(4, dataHp);
                    pstmt.setDouble(5, dataW);
                    pstmt.setDouble(6, dataA);
                    pstmt.setInt(7, dataY);
                    pstmt.setInt(8, dataO);
                    pstmt.setString(9, dataCn);
                    int rowsInserted = pstmt.executeUpdate();
                    System.out.println("Rows inserted: " + rowsInserted);
                    //("select * from Car");


                } catch (Exception e) {
                    throw new RuntimeException(e);
                }
            }


        //} catch (FileNotFoundException e) {
        //    System.out.println("An error occurred.");
        //    e.printStackTrace();
       // }
        // Parse data
        // Execute a statement
       // Statement statement = connection.createStatement();
       //  ResultSet resultSet2 = statement.executeQuery
           //    ("select * from Car;");

        // Iterate through the result and print the student names

        // Close the connection
        connection.close();
        */
        AutoProgram myFrame = new AutoProgram();

        //myFrame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        //myFrame.pack();
        myFrame.setVisible(true);
    }
}


```
### Part 2 Auto Program Class
``` java
import javax.swing.*;
import javax.swing.event.ChangeEvent;
import javax.swing.event.ChangeListener;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.sql.*;

public class AutoProgram extends JFrame implements ActionListener, ChangeListener {

    private JTextField userInputField;
    private JSlider mpgSlider;
    private JSlider hpSlider;
    private JTextArea outputArea;
    private JButton refreshButton;

    public AutoProgram() {

        setTitle("Auto Program");
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setSize(900, 650);
        setLocationRelativeTo(null);
        getContentPane().setBackground(new Color(245, 245, 245));
        setLayout(new GridBagLayout());

        GridBagConstraints gbc = new GridBagConstraints();
        gbc.insets = new Insets(10, 15, 10, 15);
        gbc.fill = GridBagConstraints.BOTH;


        JPanel inputPanel = new JPanel(new BorderLayout(5, 5));
        inputPanel.setOpaque(false);
        JLabel inputLabel = new JLabel("User Input:");
        inputPanel.add(inputLabel, BorderLayout.NORTH);

        userInputField = new JTextField("", 20);
        inputPanel.add(userInputField, BorderLayout.CENTER);
        gbc.gridx = 0; gbc.gridy = 0; gbc.weightx = 0.5; gbc.weighty = 0.0; gbc.gridwidth = 1;
        add(inputPanel, gbc);


        refreshButton = new JButton("Refresh");
        refreshButton.addActionListener(this);
        gbc.gridx = 1; gbc.gridy = 0; gbc.weightx = 0.2;
        add(refreshButton, gbc);


        JPanel slidersPanel = new JPanel(new GridLayout(1, 2, 40, 0));
        slidersPanel.setOpaque(false);


        JPanel mpgPanel = new JPanel(new BorderLayout());
        mpgPanel.setOpaque(false);
        JLabel mpgLabel = new JLabel("MPG", SwingConstants.CENTER);
        mpgSlider = new JSlider(0, 50, 0);
        setupSliderAppearance(mpgSlider, 10, 1);
        mpgSlider.addChangeListener(this);
        mpgPanel.add(mpgLabel, BorderLayout.NORTH);
        mpgPanel.add(mpgSlider, BorderLayout.CENTER);


        JPanel hpPanel = new JPanel(new BorderLayout());
        hpPanel.setOpaque(false);
        JLabel hpLabel = new JLabel("Horsepower", SwingConstants.CENTER);
        hpSlider = new JSlider(0, 250, 0);
        setupSliderAppearance(hpSlider, 25, 5);
        hpSlider.addChangeListener(this);
        hpPanel.add(hpLabel, BorderLayout.NORTH);
        hpPanel.add(hpSlider, BorderLayout.CENTER);

        slidersPanel.add(mpgPanel);
        slidersPanel.add(hpPanel);

        gbc.gridx = 0; gbc.gridy = 1; gbc.gridwidth = 2; gbc.weightx = 1.0;
        add(slidersPanel, gbc);


        JLabel infoLabel = new JLabel("Auto Info:");
        gbc.gridx = 0; gbc.gridy = 2; gbc.gridwidth = 2; gbc.weighty = 0.0;
        add(infoLabel, gbc);


        outputArea = new JTextArea();
        outputArea.setEditable(false);
        JScrollPane scrollPane = new JScrollPane(outputArea);
        scrollPane.setBorder(BorderFactory.createLineBorder(Color.GRAY));

        gbc.gridx = 0; gbc.gridy = 3; gbc.gridwidth = 2; gbc.weighty = 1.0;
        add(scrollPane, gbc);


        executeDualQueries();
    }

    private void setupSliderAppearance(JSlider slider, int majorTick, int minorTick) {
        slider.setOpaque(false);
        slider.setMajorTickSpacing(majorTick);
        slider.setMinorTickSpacing(minorTick);
        slider.setPaintTicks(true);
        slider.setPaintLabels(true);
    }

    @Override
    public void actionPerformed(ActionEvent e) {
        executeDualQueries();
    }

    @Override
    public void stateChanged(ChangeEvent e) {
        executeDualQueries();
    }


    private void executeDualQueries() {
        String inputTest = userInputField.getText().trim();
        int mpg = mpgSlider.getValue();
        int hp = hpSlider.getValue();
        boolean filterByName = !inputTest.equalsIgnoreCase("ALL") && !inputTest.isEmpty();

        StringBuilder sharedOutput = new StringBuilder();


        sharedOutput.append("==================== MPG QUERY RESULTS ( MPG: ").append(mpg).append(") ====================\n");
        String queryMpg = "SELECT mpg, cylinders, displacement, horsepower, weight, acceleration, modelYear, origin, carName FROM car WHERE mpg = ?"
                + (filterByName ? " AND carName LIKE ?" : "");

        try (Connection conn = DriverManager.getConnection("jdbc:mysql://localhost/auto", "testuser", "Pa$$word");
             PreparedStatement stmtMpg = conn.prepareStatement(queryMpg)) {

            stmtMpg.setInt(1, mpg);
            if (filterByName) {
                stmtMpg.setString(2, "%" + inputTest + "%");
            }
            try (ResultSet rsMpg = stmtMpg.executeQuery()) {
                appendResultSetToStringBuilder(rsMpg, sharedOutput);
            }
        } catch (SQLException ex) {
            sharedOutput.append("MPG Database Error: ").append(ex.getMessage()).append("\n");
        }

        sharedOutput.append("\n\n");


        sharedOutput.append("==================== HORSEPOWER QUERY RESULTS (HP: ").append(hp).append(") ====================\n");
        String queryHp = "SELECT mpg, cylinders, displacement, horsepower, weight, acceleration, modelYear, origin, carName FROM car WHERE horsepower = ?"
                + (filterByName ? " AND carName LIKE ?" : "");

        try (Connection conn = DriverManager.getConnection("jdbc:mysql://localhost/auto","testuser", "Pa$$word");
             PreparedStatement stmtHp = conn.prepareStatement(queryHp)) {

            stmtHp.setInt(1, hp);
            if (filterByName) {
                stmtHp.setString(2, "%" + inputTest + "%");
            }
            try (ResultSet rsHp = stmtHp.executeQuery()) {
                appendResultSetToStringBuilder(rsHp, sharedOutput);
            }
        } catch (SQLException ex) {
            sharedOutput.append("Horsepower Database Error: ").append(ex.getMessage()).append("\n");
        }


        outputArea.setText(sharedOutput.toString());
    }


    private void appendResultSetToStringBuilder(ResultSet rs, StringBuilder sb) throws SQLException {
        boolean hasRecords = false;
        while (rs.next()) {
            hasRecords = true;
            String row = String.format("%-5.1f %-2d  %-5.1f  %-5.1f  %-5.0f  %-4.1f  %-2d.  %-2d.       \"%s\"\n",
                    rs.getDouble("mpg"),
                    rs.getInt("cylinders"),
                    rs.getDouble("displacement"),
                    rs.getDouble("horsepower"),
                    rs.getDouble("weight"),
                    rs.getDouble("acceleration"),
                    rs.getInt("modelYear"),
                    rs.getInt("origin"),
                    rs.getString("carName")
            );
            sb.append(row);
        }
        if (!hasRecords) {
            sb.append("(No vehicles found matching criteria)\n");
        }
    }}
```
## Results and Table Schema
<img width="753" height="345" alt="Screenshot 2026-05-24 205610" src="https://github.com/user-attachments/assets/f5ea4bcf-3b52-4cf4-8972-a470cddcabda" />
<img width="1103" height="797" alt="Screenshot 2026-05-24 204615" src="https://github.com/user-attachments/assets/f5bd8ced-b578-4362-a2b7-574c0b620705" />
<img width="1087" height="763" alt="Screenshot 2026-05-24 204544" src="https://github.com/user-attachments/assets/b714c7e6-7653-489d-9249-563a029fda62" />
<img width="1095" height="797" alt="Screenshot 2026-05-24 204524" src="https://github.com/user-attachments/assets/8b628d87-4d6b-4613-a32e-55cb612ad603" />

## Video
https://www.youtube.com/watch?v=kJyrelbwRYs
