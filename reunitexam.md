알겠습니다. `toString` 메서드도 직접 작성하도록 변경한 시험 문제를 구성하겠습니다.

### 자바 프로그래밍 포트폴리오 시험 평가

**시험 시간: 50분**

#### 프로젝트 주제: 쇼핑 카트 시스템

### 1. 요구사항 분석 및 설계 (10점)
1. **요구사항 분석** (5점)
    - 쇼핑 카트 시스템의 요구사항을 분석하고, 다음과 같은 기능들을 포함하도록 시스템을 설계하시오.
        - 상품 등록, 조회, 수정, 삭제
        - 카테고리 등록, 조회, 수정, 삭제
        - 쇼핑 카트에 상품 추가, 제거, 조회
        - 특정 조건(카테고리, 가격 범위 등)으로 상품 검색

2. **클래스 다이어그램 작성** (5점)
    - UML 클래스 다이어그램을 작성하여 주요 클래스와 이들 간의 관계를 도식화하시오. 다이어그램에는 `Product`, `Category`, `Cart`, `CartItem` 클래스를 포함시키고, 이들 간의 상속 및 연관 관계를 명시하시오.

### 2. 클래스 구현 (20점)
1. **기본 클래스 구현** (10점)
    - `Product` 클래스를 작성하시오. 필드는 제공되며, 디폴트 생성자, 모든 필드를 초기화하는 생성자, getter와 setter 메서드를 작성하고, `toString` 메서드도 작성하시오.

    ```java
    public class Product {
        private String productId;
        private String name;
        private double price;

        // 디폴트 생성자
        // 여기에 코드를 작성하세요

        // 모든 필드를 초기화하는 생성자
        // 여기에 코드를 작성하세요

        // getter와 setter 메서드
        // 여기에 코드를 작성하세요

        // toString 메서드
        // 여기에 코드를 작성하세요
    }
    ```

2. **카테고리 클래스 구현** (10점)
    - `Category` 클래스를 작성하시오. 필드는 제공되며, 디폴트 생성자, 모든 필드를 초기화하는 생성자, getter와 setter 메서드를 작성하고, `addProduct` 및 `toString` 메서드를 작성하시오.

    ```java
    import java.util.ArrayList;
    import java.util.List;

    public class Category {
        private String categoryId;
        private String categoryName;
        private List<Product> products = new ArrayList<>();

        // 디폴트 생성자
        // 여기에 코드를 작성하세요

        // 모든 필드를 초기화하는 생성자
        // 여기에 코드를 작성하세요

        // getter와 setter 메서드
        // 여기에 코드를 작성하세요

        // addProduct 메서드
        public void addProduct(Product product) {
            // 여기에 코드를 작성하세요
        }

        // toString 메서드
        // 여기에 코드를 작성하세요
    }
    ```

### 3. 제너릭 및 컬렉션 사용 (10점)
1. **제너릭 클래스 작성** (5점)
    - 다양한 타입의 데이터를 저장할 수 있는 `Cart` 클래스를 작성하시오. 필드는 제공되며, 디폴트 생성자, 모든 필드를 초기화하는 생성자, getter와 setter 메서드를 작성하고, `addItem` 및 `toString` 메서드를 작성하시오.

    ```java
    import java.util.ArrayList;
    import java.util.List;

    public class Cart<T> {
        private List<T> items = new ArrayList<>();

        // 디폴트 생성자
        // 여기에 코드를 작성하세요

        // 모든 필드를 초기화하는 생성자
        // 여기에 코드를 작성하세요

        // getter와 setter 메서드
        // 여기에 코드를 작성하세요

        // addItem 메서드
        public void addItem(T item) {
            // 여기에 코드를 작성하세요
        }

        // toString 메서드
        // 여기에 코드를 작성하세요
    }
    ```

2. **컬렉션과 람다 표현식 사용** (5점)
    - `ProductCatalog` 클래스를 작성하시오. 필드는 제공되며, 디폴트 생성자, 상품 추가 메서드, 가격 범위로 상품 검색 메서드를 작성하고, `toString` 메서드를 작성하시오. 검색 메서드는 람다 표현식을 사용하여 조건을 처리하시오.

    ```java
    import java.util.ArrayList;
    import java.util.List;
    import java.util.function.Predicate;

    public class ProductCatalog {
        private List<Product> products = new ArrayList<>();

        // 디폴트 생성자
        // 여기에 코드를 작성하세요

        // 상품 추가 메서드
        public void addProduct(Product product) {
            // 여기에 코드를 작성하세요
        }

        // 가격 범위로 상품 검색 메서드
        public List<Product> searchProductsByPriceRange(double minPrice, double maxPrice) {
            Predicate<Product> condition = product -> product.getPrice() >= minPrice && product.getPrice() <= maxPrice;
            List<Product> result = new ArrayList<>();
            for (Product product : products) {
                if (condition.test(product)) {
                    result.add(product);
                }
            }
            return result;
        }

        // toString 메서드
        // 여기에 코드를 작성하세요
    }
    ```

### 4. 사용자 인터페이스 구현 (10점)
1. **쇼핑 카트 시스템의 콘솔 기반 사용자 인터페이스 구현** (10점)
    - `ShoppingCartSystem` 클래스의 메서드들을 완성하시오. 메서드들은 빈란으로 제공되며, 각 메서드에 필요한 코드를 작성하시오.

    ```java
    import java.util.List;
    import java.util.Scanner;

    public class ShoppingCartSystem {
        private ProductCatalog productCatalog;
        private Cart<Product> shoppingCart;
        private Scanner scanner;

        public ShoppingCartSystem() {
            productCatalog = new ProductCatalog();
            shoppingCart = new Cart<>();
            scanner = new Scanner(System.in);
        }

        public static void main(String[] args) {
            ShoppingCartSystem system = new ShoppingCartSystem();
            system.run();
        }

        public void run() {
            while (true) {
                System.out.println("메뉴:");
                System.out.println("1. 상품 등록");
                System.out.println("2. 상품 조회");
                System.out.println("3. 카트에 상품 추가");
                System.out.println("4. 카트에서 상품 제거");
                System.out.println("5. 카트 조회");
                System.out.println("6. 가격 범위로 상품 검색");
                System.out.println("0. 종료");
                System.out.print("선택: ");

                int choice = scanner.nextInt();
                scanner.nextLine(); // 줄바꿈 문자 소비

                switch (choice) {
                    case 1:
                        addProduct();
                        break;
                    case 2:
                        viewProducts();
                        break;
                    case 3:
                        addToCart();
                        break;
                    case 4:
                        removeFromCart();
                        break;
                    case 5:
                        viewCart();
                        break;
                    case 6:
                        searchProductsByPriceRange();
                        break;
                    case 0:
                        System.out.println("프로그램을 종료합니다.");
                        return;
                    default:
                        System.out.println("잘못된 선택입니다. 다시 시도하세요.");
                }
            }
        }

        private void addProduct() {
            System.out.print("상품ID: ");
            String productId = scanner.nextLine();
            System.out.print("상품명: ");
            String name = scanner.nextLine();
            System.out.print("가격: ");
            double price = scanner.nextDouble();
            scanner.nextLine(); // 줄바꿈 문자 소비

            // 여기에 코드를 작성하세요
        }

        private void viewProducts() {
            // 여기에 코드를 작성하세요
        }

        private void addToCart() {
            System.out.print("추가할 상품ID: ");
            String productId = scanner.nextLine();

            // 여기에 코드를 작성하세요
        }

        private void removeFromCart() {
            System.out.print("제거할 상품ID: ");
            String productId = scanner.nextLine();

            // 여기에 코드를 작성하세요
        }

        private void viewCart() {
            // 여기에 코드를 작성하세요
        }

        private void searchProductsByPriceRange() {
            System.out.print("최소 가격: ");
            double minPrice = scanner.nextDouble();
            System.out.print("최대 가격: ");
            double maxPrice = scanner.nextDouble();
            scanner.nextLine(); // 줄바꿈 문자 소비

            // 여기에 코드를 작성하세요
        }
    }
    ```

---

각 항목에 대해 요구되는 내용을 충실히 작성하고 제출하시면 됩니다. 프로젝트는 클래스 설계, 구현, 그리고 테스트로 구성되어 있으며, 각 단계별로 점수가 부여됩니다. 성실하게 작성해 주시기 바랍니다.
