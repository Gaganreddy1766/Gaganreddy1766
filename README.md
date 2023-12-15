import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

class Product {
    private String name;
    private double price;

    public Product(String name, double price) {
        this.name = name;
        this.price = price;
    }

    public String getName() {
        return name;
    }

    public double getPrice() {
        return price;
    }
}

class ShoppingCart {
    private List<Product> items = new ArrayList<>();

    public void addItem(Product product) {
        items.add(product);
    }

    public List<Product> getItems() {
        return items;
    }

    public double calculateTotal() {
        double total = 0;
        for (Product item : items) {
            total += item.getPrice();
        }
        return total;
    }
}

public class AmazonShoppingApp {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        ShoppingCart cart = new ShoppingCart();

        while (true) {
            System.out.println("Welcome to Amazon Shopping!");
            System.out.println("1. Add Product to Cart");
            System.out.println("2. View Cart");
            System.out.println("3. Checkout");
            System.out.println("4. Exit");

            int choice = scanner.nextInt();

            switch (choice) {
                case 1:
                    System.out.println("Enter Product Name:");
                    String productName = scanner.next();
                    System.out.println("Enter Product Price:");
                    double productPrice = scanner.nextDouble();
                    Product product = new Product(productName, productPrice);
                    cart.addItem(product);
                    System.out.println(productName + " added to cart!");
                    break;
                case 2:
                    System.out.println("Shopping Cart:");
                    for (Product item : cart.getItems()) {
                        System.out.println(item.getName() + " - $" + item.getPrice());
                    }
                    System.out.println("Total: $" + cart.calculateTotal());
                    break;
                case 3:
                    System.out.println("Checkout successful!");
                    System.out.println("Total Amount: $" + cart.calculateTotal());
                    System.exit(0);
                case 4:
                    System.exit(0);
                default:
                    System.out.println("Invalid choice. Please try again.");
            }
        }
    }
}
