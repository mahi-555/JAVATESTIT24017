# JAVATESTIT24017
# TASK 1 :
<img width="1281" height="762" alt="Screenshot 2026-11-01 105758" src="https://github.com/user-attachments/assets/5078bb69-296c-4beb-a84b-ed8fe53abcc5" />












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
