package expensemanagementsystem;

import javax.swing.*;
import java.awt.*;
import java.time.LocalDate;
import java.util.ArrayList;
import java.util.Iterator;

public class Main {

    // Expense variables
    private static ArrayList<Expense> expenseList = new ArrayList<>();
    private static int counter = 1;

    // Expense inner class
    static class Expense {
        private int expenseId;
        private double amount;
        private String category;
        private LocalDate date;
        private String paymentMode;

        public Expense(double amount, String category, LocalDate date, String paymentMode) {
            this.expenseId = counter++;
            this.amount = amount;
            this.category = category;
            this.date = date;
            this.paymentMode = paymentMode;
        }

        public int getExpenseId() { return expenseId; }
        public double getAmount() { return amount; }

        public String toString() {
            return "ID: " + expenseId +
                    " | Amount: " + amount +
                    " | Category: " + category +
                    " | Date: " + date +
                    " | Payment: " + paymentMode;
        }
    }

    public static void main(String[] args) {

        JFrame frame = new JFrame("Expense Management System");
        frame.setSize(400, 300);
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setLayout(new GridLayout(4, 1));

        JButton addButton = new JButton("Add Expense");
        JButton viewButton = new JButton("View Expenses");
        JButton deleteButton = new JButton("Delete Expense");
        JButton exitButton = new JButton("Exit");

        frame.add(addButton);
        frame.add(viewButton);
        frame.add(deleteButton);
        frame.add(exitButton);

        // ADD EXPENSE
        addButton.addActionListener(e -> {
            try {
                double amount = Double.parseDouble(
                        JOptionPane.showInputDialog("Enter Amount:")
                );

                String category = JOptionPane.showInputDialog("Enter Category:");
                LocalDate date = LocalDate.parse(
                        JOptionPane.showInputDialog("Enter Date (yyyy-mm-dd):")
                );
                String payment = JOptionPane.showInputDialog("Enter Payment Mode:");

                expenseList.add(new Expense(amount, category, date, payment));

                JOptionPane.showMessageDialog(frame, "Expense Added Successfully!");

            } catch (Exception ex) {
                JOptionPane.showMessageDialog(frame, "Invalid Input!");
            }
        });

        // VIEW EXPENSES
        viewButton.addActionListener(e -> {
            if (expenseList.isEmpty()) {
                JOptionPane.showMessageDialog(frame, "No expenses found.");
                return;
            }

            StringBuilder sb = new StringBuilder();
            double total = 0;

            for (Expense e1 : expenseList) {
                sb.append(e1).append("\n");
                total += e1.getAmount();
            }

            sb.append("\nTotal Expense: ").append(total);

            JTextArea area = new JTextArea(sb.toString());
            area.setEditable(false);

            JOptionPane.showMessageDialog(frame, new JScrollPane(area));
        });

        // DELETE EXPENSE
        deleteButton.addActionListener(e -> {
            try {
                int id = Integer.parseInt(
                        JOptionPane.showInputDialog("Enter Expense ID to Delete:")
                );

                Iterator<Expense> iterator = expenseList.iterator();
                boolean found = false;

                while (iterator.hasNext()) {
                    Expense ex = iterator.next();
                    if (ex.getExpenseId() == id) {
                        iterator.remove();
                        found = true;
                        break;
                    }
                }

                if (found)
                    JOptionPane.showMessageDialog(frame, "Deleted Successfully!");
                else
                    JOptionPane.showMessageDialog(frame, "ID Not Found!");

            } catch (Exception ex) {
                JOptionPane.showMessageDialog(frame, "Invalid ID!");
            }
        });

        exitButton.addActionListener(e -> System.exit(0));

        frame.setVisible(true);
    }
}
