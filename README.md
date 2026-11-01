# JAVATESTIT24017
# TASK 1 :
<img width="1281" height="762" alt="Screenshot 2026-11-01 105758" src="https://github.com/user-attachments/assets/5078bb69-296c-4beb-a84b-ed8fe53abcc5" />

# Task 2 :
# code
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.util.Scanner;

public class Main {

    public static boolean isPrime(int number) {

        if (number < 2) {
            return false;
        }

        for (int i = 2; i <= number / i; i++) {
            if (number % i == 0) {
                return false;
            }
        }

        return true;
    }

    public static int findNthPrime(int n) {

        int count = 0;
        int number = 1;

        while (count < n) {
            number++;

            if (isPrime(number)) {
                count++;
            }
        }

        return number;
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        System.out.print("Enter N: ");
        int n = sc.nextInt();

        if (n <= 0) {
            System.out.println("Please enter a positive number.");
            sc.close();
            return;
        }

        int prime = findNthPrime(n);

        System.out.println("The " + n +
                "th Prime Number is: " + prime);

        String url = "jdbc:mysql://localhost:3306/prime_db";
        String username = "root";
        String password = "mahin555";

        String sql = "INSERT INTO prime_numbers " +
                "(n_value, prime_number) VALUES (?, ?)";

        try {
            Connection con = DriverManager.getConnection(
                    url, username, password);

            PreparedStatement ps = con.prepareStatement(sql);

            ps.setInt(1, n);
            ps.setInt(2, prime);

            ps.executeUpdate();

            System.out.println("Data inserted successfully!");

            ps.close();
            con.close();

        } catch (Exception e) {
            System.out.println("Database Error: " + e.getMessage());
        }

        sc.close();
    }
}

# output
<img width="1863" height="906" alt="nthprimechecker" src="https://github.com/user-attachments/assets/7dbfe651-40aa-42bf-8b05-8bab893da7de" />










# TASK 3 :
<img width="1077" height="881" alt="Screenshot 2026-11-01 141405" src="https://github.com/user-attachments/assets/7591b128-435e-424a-a2e5-8dbbf17d0c5d" />

# HelloWorld Servlet code : 
package com.primes;

import java.io.IOException;

import jakarta.servlet.ServletException;
import jakarta.servlet.annotation.WebServlet;
import jakarta.servlet.http.HttpServlet;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;

@WebServlet("/")
public class HelloServlet extends HttpServlet {

    @Override
    protected void doPost(HttpServletRequest request,
                          HttpServletResponse response)
            throws ServletException, IOException {

        response.setContentType("text/html;charset=UTF-8");

        String numberStr = request.getParameter("number");

        try {

            long number = Long.parseLong(numberStr);

            boolean isPrime = true;

            if (number <= 1) {
                isPrime = false;
            } else {

                for (long i = 2; i <= number / i; i++) {

                    if (number % i == 0) {
                        isPrime = false;
                        break;
                    }
                }
            }

            String result;

            if (isPrime) {
                result = number + " is a Prime Number!";
            } else {
                result = number + " is Not a Prime Number!";
            }

            request.setAttribute("result", result);

        } catch (NumberFormatException e) {

            request.setAttribute("result",
                    "Please enter a valid whole number.");

        }

        request.getRequestDispatcher("index.jsp")
                .forward(request, response);
    }
}


# Task 4 :
<img width="1795" height="922" alt="Screenshot 2026-11-01 141248" src="https://github.com/user-attachments/assets/4848db0d-df79-46ec-945e-943d82054a31" />
