import java.util.*;
class Product {
    String id;
    String name;
    double price;

    Product(String id, String name, double price) {
        this.id = id;
        this.name = name;
        this.price = price;
    }
}
class ProductDatabase {
    Map<String, Product> products = new HashMap<>();

    ProductDatabase() {
        products.put("P-1", new Product("P-1", "Noodles", 50));
        products.put("P-2", new Product("P-2", "Biscuits", 30));
        products.put("P-3", new Product("P-3", "Juice", 80));
    }

    Product getProduct(String id) {
        return products.get(id);
    }

    void displayProducts() {
        System.out.println("Available Products:");
        for (Product p : products.values()) {
            System.out.println(p.id + ": " + p.name + " - Rs " + p.price);
        }
    }
}
class ShoppingCart {
    List<Product> cart = new ArrayList<>();

    void addProduct(Product p) {
        cart.add(p);
    }

    void showCart() {
        System.out.println("\nYour Cart:");
        for (Product p : cart) {
            System.out.println(p.name + " - Rs " + p.price);
        }
    }

    double calculateTotal() {
        double total = 0;
        for (Product p : cart) {
            total += p.price;
        }
        return total;
    }
}
class PaymentGateway {
    boolean processPayment(double amount) {
            return true;
    }
}
class ShoppingCartController {
    ProductDatabase db;
    ShoppingCart cart;
    PaymentGateway gateway;

    ShoppingCartController() {
        db = new ProductDatabase();
        cart = new ShoppingCart();
        gateway = new PaymentGateway();
    }

    void addToCart(String productId) {
        Product p = db.getProduct(productId);
        if (p != null) {
            cart.addProduct(p);
            System.out.println(p.name + " added to cart.");
        } else {
            System.out.println("Product not found.");
        }
    }

    void checkout() {
        double total = cart.calculateTotal();
        cart.showCart();
        System.out.println("Total: Rs " + total);
        if (gateway.processPayment(total)) {
            System.out.println("Payment successful. Thank you!");
        } else {
            System.out.println("Payment failed. Try again.");
        }
    }

    void showProducts() {
        db.displayProducts();
    }
}
public class ShoppingAssistanceSystem {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        ShoppingCartController controller = new ShoppingCartController();
        String choice;

        System.out.println("Welcome to Shopping Assistance System!");

        do {
            controller.showProducts();
            System.out.print("Enter product ID to add to cart (or 'checkout' to pay): ");
            choice = sc.nextLine().trim();

            if (choice.equalsIgnoreCase("checkout")) {
                controller.checkout();
                break;
            } else {
                controller.addToCart(choice);
            }
        } while (true);

        sc.close();
    }
}
