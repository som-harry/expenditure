# Expenditure

> A Vue.js project that calculates the total amount of items

# install dependencies
npm install -g vue cli

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# How it works
add item and price using the add button
click on the added items to calculate the total amount of items added
unclick an item to subtract its value from the total amount.

# How it was built
i. Two static components are added by default but their individual value are not added to the total amount until any component is clicked
a. The above components have a click listener that adds/subtracts the individual value to the total amount
b. When the component is clicked, its color changes to green and the value is added to total.
c. When the component is clicked again, its color changes to pink (which is the default color for components) and its value is subtracted from total
d. The change in color onclcik is as a result of the styling class being bind to a boolean

ii. All dynamic components that will be added by user also have the above features.
iii. The total value is added/subtracted when components is/are clicked.


# Note to developer
used the styling for the static component for the dynamic component(slot)
