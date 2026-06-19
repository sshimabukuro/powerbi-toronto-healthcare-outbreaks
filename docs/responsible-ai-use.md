# Responsible Use of AI

## Overview

I used ChatGPT as an AI-assisted learning and development tool while building this Power BI dashboard.

AI was used to support the development process, but it did not replace my own review, testing, or decision-making.

## How AI Was Used

ChatGPT was used to help with:

* brainstorming dashboard ideas
* organizing the dashboard layout
* reviewing possible DAX measures
* thinking through data modelling options
* comparing whether date attributes should be stored in the outbreak table or handled through a Calendar table
* planning the visual build order
* improving the written case study and GitHub documentation

## Human Review and Validation

I did not apply AI suggestions automatically.

I reviewed the recommendations, tested them in Power BI, and validated decisions against:

* the dataset documentation
* the dashboard objective
* Power BI modelling best practices
* the results shown in the report visuals

## Example of Critical Review

One example was the decision to keep `Coronavirus*` separate from `COVID-19`.

At first, it could seem reasonable to group these values together. However, the dataset documentation explains that `Coronavirus*` refers to seasonal coronavirus and not COVID-19.

Because of that, I kept the two values separate in the analysis.

This helped preserve the meaning of the original data and avoid overstating COVID-19-related outbreaks.

## Value of AI in the Project

Using AI helped me move faster and structure the work more clearly.

However, the final modelling decisions, dashboard structure, DAX logic, and interpretation of results were reviewed and validated as part of the analysis process.
