# J Spinner Miles to km conversion
## Code
``` java
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

public class MilesFrame extends JFrame implements ChangeListener {
    private JSpinner mileSpinner;    // miles
    private JTextField kMField; // Displays km
    private JLabel mileLabel;        // Label for miles
    private JLabel kMLabel;     // Label for km

    /* Constructor creates GUI components and adds GUI components
       using a GridBagLayout. */
    MilesFrame() {
        int initMile;     // Spinner initial value display
        int minMile;      // Spinner min value
        int maxMile;      // Spinner max value
        int stepVal;      // Spinner step

        initMile = 0;
        minMile = 0;
        maxMile = 1000;
        stepVal = 1;

        // Used to specify GUI component layout
        GridBagConstraints layoutConst = null;

        // Specifies the types of values displayed in spinner
        SpinnerNumberModel spinnerModel = null;

        // Set frame's title
        setTitle("Enter miles to convert to KM!");

        // Create labels
        mileLabel = new JLabel("Select Miles");
        kMLabel = new JLabel("Distance in KM");

        // Create a spinner model, the spinner, and set the change listener
        spinnerModel = new SpinnerNumberModel(initMile, minMile, maxMile, stepVal);
        mileSpinner = new JSpinner(spinnerModel);
        mileSpinner.addChangeListener(this);

        // Create field
        kMField = new JTextField(15);
        kMField.setEditable(false);
        kMField.setText("0 - 1000");

        // Use a GridBagLayout
        setLayout(new GridBagLayout());

        // Specify component's grid location
        layoutConst = new GridBagConstraints();
        layoutConst.insets = new Insets(10, 10, 10, 1);
        layoutConst.anchor = GridBagConstraints.LINE_END;
        layoutConst.gridx = 0;
        layoutConst.gridy = 0;
        add(mileLabel, layoutConst);

        layoutConst = new GridBagConstraints();
        layoutConst.insets = new Insets(10, 1, 10, 10);
        layoutConst.fill = GridBagConstraints.HORIZONTAL;
        layoutConst.gridx = 1;
        layoutConst.gridy = 0;
        add(mileSpinner, layoutConst);

        layoutConst = new GridBagConstraints();
        layoutConst.insets = new Insets(10, 10, 10, 1);
        layoutConst.anchor = GridBagConstraints.LINE_END;
        layoutConst.gridx = 0;
        layoutConst.gridy = 1;
        add(kMLabel, layoutConst);

        layoutConst = new GridBagConstraints();
        layoutConst.insets = new Insets(10, 1, 10, 10);
        layoutConst.fill = GridBagConstraints.HORIZONTAL;
        layoutConst.gridx = 1;
        layoutConst.gridy = 1;
        add(kMField, layoutConst);
    }

    @Override
    public void stateChanged(ChangeEvent event) {
        Integer miles;     // Dog age input

        miles = (Integer) mileSpinner.getValue();

        // Choose output based on miles
        kMField.setText(String.valueOf(miles*1.6));

    }

    /* Creates a DogYearsFrame and makes it visible */
    public static void main(String[] args) {
        // Creates DogYearsFrame and its components
        MilesFrame myFrame = new MilesFrame();

        myFrame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        myFrame.pack();
        myFrame.setVisible(true);
    }
}
```
