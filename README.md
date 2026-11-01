## IT-24035

package com.example.demo;

import java.io.IOException;
import java.io.PrintWriter;
import jakarta.servlet.ServletException;
import jakarta.servlet.annotation.WebServlet;
import jakarta.servlet.http.HttpServlet;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;

@WebServlet("/check-prime")
public class PrimeCheckServlet extends HttpServlet {
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        response.setContentType("text/html;charset=UTF-8");
        PrintWriter out = response.getWriter();

        String numParam = request.getParameter("num");

        out.println("<h2>Prime Number Verification</h2>");

        if (numParam != null) {
            try {
                int n = Integer.parseInt(numParam);
                boolean isPrime = true;

                if (n <= 1) {
                    isPrime = false;
                } else {
                    for (int i = 2; i <= Math.sqrt(n); i++) {
                        if (n % i == 0) {
                            isPrime = false;
                            break;
                        }
                    }
                }

                if (isPrime) {
                    out.println("<h3 style='color:green;'>" + n + " is a Prime Number!</h3>");
                } else {
                    out.println("<h3 style='color:red;'>" + n + " is NOT a Prime Number.</h3>");
                }

            } catch (NumberFormatException e) {
                out.println("<p style='color:red;'>Please enter a valid integer number!</p>");
            }
        } else {
            out.println("<p>Please provide a number in the URL, e.g., <b>?num=17</b></p>");
        }
    }
}


<img width="495" height="236" alt="Screenshot 2026-11-01 112101" src="https://github.com/user-attachments/assets/14162d44-2588-405f-9777-4b4d5f78271c" />
