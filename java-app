import com.fazecast.jSerialComm.SerialPort;
import javax.swing.*;

public class TrafficGUI {

    // SERIAL PORT
    static SerialPort port;

    public static void main(String[] args) {

        // =========================
        // FRAME
        // =========================
        JFrame frame = new JFrame("Traffic Light Control System");

        frame.setSize(450, 350);

        frame.setLayout(null);

        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

        // =========================
        // TITLE
        // =========================
        JLabel title = new JLabel("TRAFFIC LIGHT CONTROLLER");

        title.setBounds(100, 10, 250, 30);

        frame.add(title);

        // =========================
        // CONNECT BUTTON
        // =========================
        JButton connectBtn = new JButton("CONNECT");

        connectBtn.setBounds(140, 50, 150, 40);

        frame.add(connectBtn);

        // =========================
        // RED BUTTON
        // =========================
        JButton redBtn = new JButton("RED");

        redBtn.setBounds(30, 120, 100, 50);

        frame.add(redBtn);

        // =========================
        // YELLOW BUTTON
        // =========================
        JButton yellowBtn = new JButton("YELLOW");

        yellowBtn.setBounds(160, 120, 100, 50);

        frame.add(yellowBtn);

        // =========================
        // GREEN BUTTON
        // =========================
        JButton greenBtn = new JButton("GREEN");

        greenBtn.setBounds(290, 120, 100, 50);

        frame.add(greenBtn);

        // =========================
        // STANDARD CHECK BUTTON
        // =========================
        JButton checkBtn = new JButton("STANDARD CHECK");

        checkBtn.setBounds(100, 200, 220, 50);

        frame.add(checkBtn);

        // =========================
        // STATUS LABEL
        // =========================
        JLabel status = new JLabel("STATUS: DISCONNECTED");

        status.setBounds(120, 270, 250, 30);

        frame.add(status);

        // =========================
        // CONNECT BUTTON ACTION
        // =========================
        connectBtn.addActionListener(e -> {

            // CHANGE THIS TO YOUR PORT
            port = SerialPort.getCommPort("COM5");

            port.setBaudRate(9600);

            if (port.openPort()) {

                try {

                    // IMPORTANT DELAY
                    Thread.sleep(2000);

                } catch (Exception ex) {

                    ex.printStackTrace();
                }

                status.setText("STATUS: CONNECTED");

                System.out.println("CONNECTED SUCCESSFULLY");

            } else {

                status.setText("STATUS: CONNECTION FAILED");

                System.out.println("FAILED TO CONNECT");
            }
        });

        // =========================
        // RED BUTTON ACTION
        // =========================
        redBtn.addActionListener(e -> {

            sendCommand("RED");
        });

        // =========================
        // YELLOW BUTTON ACTION
        // =========================
        yellowBtn.addActionListener(e -> {

            sendCommand("YELLOW");
        });

        // =========================
        // GREEN BUTTON ACTION
        // =========================
        greenBtn.addActionListener(e -> {

            sendCommand("GREEN");
        });

        // =========================
        // STANDARD CHECK BUTTON
        // =========================
        checkBtn.addActionListener(e -> {

            sendCommand("CHECK");
        });

        // =========================
        // SHOW FRAME
        // =========================
        frame.setVisible(true);
    }

    // =========================
    // SEND COMMAND FUNCTION
    // =========================
    static void sendCommand(String command) {

        if (port != null && port.isOpen()) {

            String text = command + "\n";

            port.writeBytes(text.getBytes(), text.length());

            System.out.println("SENT: " + command);

        } else {

            System.out.println("PORT NOT OPEN");
        }
    }
}
