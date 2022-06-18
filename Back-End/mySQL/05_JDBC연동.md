# DB 생성하기

    mysql> CREATE DATABASE {DB이름};

# Table 생성

workbench이용


# eclipse와 DB 연동하기

    private Connection conn;
        private static final String USERNAME = "root";
        private static final String PASSWORD = "1234";
        private static final String URL = "jdbc:mysql://localhost/book?serverTimezone=UTC";
        

        public BookDAO() {
            try {
                Class.forName("com.mysql.cj.jdbc.Driver");
                conn = DriverManager.getConnection(URL, USERNAME, PASSWORD);
                System.out.println("드라이버 로딩 성공");
            } catch (Exception e) {
                System.out.println("드라이버 로딩 실패 ");
                try {
                    conn.close();
                } catch (SQLException e1) {
                }
            }



# eclipse에서 테이블 insert 하기

DAO 와 DTO 메소드를 이용한다.

DTO : 데이터 관리
DAO : 데이터 

    import java.sql.Connection;
    import java.sql.DriverManager;
    import java.sql.PreparedStatement;
    import java.sql.SQLException;
    import java.sql.Statement;
    import java.sql.ResultSet;

    public class BookDAO {
        private Connection conn;
        private static final String USERNAME = "root";
        private static final String PASSWORD = "1234";
        private static final String URL = "jdbc:mysql://localhost/book?serverTimezone=UTC";
        

        public BookDAO() {
            try {
                Class.forName("com.mysql.cj.jdbc.Driver");
                conn = DriverManager.getConnection(URL, USERNAME, PASSWORD);
                System.out.println("드라이버 로딩 성공");
            } catch (Exception e) {
                System.out.println("드라이버 로딩 실패 ");
                try {
                    conn.close();
                } catch (SQLException e1) {
                }
            }
        }
        
        private Connection getConnection() throws SQLException {
            Connection conn = null;
            
            try {
                Class.forName("com.mysql.cj.jdbc.Driver");
                conn = DriverManager.getConnection(URL, USERNAME, PASSWORD);
            }
            catch (ClassNotFoundException e) {
                System.out.println(" 드라이버 로딩 실패 ");
            }
            
            return conn;
        }


        public void insertBook(BookDTO bookDTO) {
            boolean result = false;
            Connection conn = null;
            PreparedStatement pstmt = null;

            try {
                conn = getConnection();

                // Column
                // PK , name , email , password
                String sql = "INSERT INTO book VALUES (?, ?, ?, ?, ?, ?);";
                pstmt = conn.prepareStatement(sql);

                pstmt.setString(1, bookDTO.getBookNo());
                pstmt.setString(2, bookDTO.getBookTitle());
                pstmt.setString(3, bookDTO.getBookAuthor());
                pstmt.setInt(4, bookDTO.getBookYear());
                pstmt.setInt(5, bookDTO.getBookPrice());
                pstmt.setString(6, bookDTO.getBookPublisher());
                int count = pstmt.executeUpdate();

                result = (count == 1);
            } catch (SQLException e) {
                e.printStackTrace();
            } finally {
                try {
                    if (conn != null) {
                        conn.close();
                    }
                    if (pstmt != null) {
                        pstmt.close();
                    }
                } catch (SQLException e) {
                    e.printStackTrace();
                }
            }
        }



        public void selectBook() {
            Connection conn = null;
            Statement stmt = null;
            ResultSet rs = null;

            try {
                Class.forName("com.mysql.cj.jdbc.Driver");
                conn = DriverManager.getConnection(URL, USERNAME, PASSWORD);

                // 쿼리 수행을 위한 Statement 객체 생성
                stmt = conn.createStatement();

                String sql = "SELECT* FROM book";

                // 쿼리 수행
                // 레코드들은 ResultSet 객체에 추가된다.
                rs = stmt.executeQuery(sql);

                // 실행결과 출력하기
                while (rs.next()) {
                    String num = rs.getString(1);
                    String title = rs.getString(2);
                    String author = rs.getString(3);
                    String year = rs.getString(4);
                    String price = rs.getString(5);
                    String publisher = rs.getString(6);

                    System.out.println(num + "\t" + title + "\t" + author + "\t" + year + "\t" + price + "\t" + publisher);
                }
            } catch (ClassNotFoundException e) {
                System.out.println("드라이버 로딩 실패");
            } catch (SQLException e) {
                System.out.println("에러 " + e);
            } finally {
                try {
                    if (conn != null && !conn.isClosed()) {
                        conn.close();
                    }
                    if (stmt != null && !stmt.isClosed()) {
                        stmt.close();
                    }
                    if (rs != null && !rs.isClosed()) {
                        rs.close();
                    }
                } catch (SQLException e) {
                    e.printStackTrace();
                }
            }

        }
    }



BookDTO

    public class BookDTO {
        private String bookNo;
        private String bookTitle;
        private String bookAuthor;
        private int bookYear;
        private int bookPrice;
        private String bookPublisher;
        

        
        //start get , set

        public String getBookNo() {
            return bookNo;
        }

        public void setBookNo(String bookNo) {
            this.bookNo = bookNo;
        }

        public String getBookTitle() {
            return bookTitle;
        }

        public void setBookTitle(String bookTitle) {
            this.bookTitle = bookTitle;
        }

        public String getBookAuthor() {
            return bookAuthor;
        }

        public void setBookAuthor(String bookAuthor) {
            this.bookAuthor = bookAuthor;
        }

        public int getBookYear() {
            return bookYear;
        }

        public void setBookYear(int bookYear) {
            this.bookYear = bookYear;
        }

        public int getBookPrice() {
            return bookPrice;
        }

        public void setBookPrice(int bookPrice) {
            this.bookPrice = bookPrice;
        }

        public String getBookPublisher() {
            return bookPublisher;
        }

        public void setBookPublisher(String bookPublisher) {
            this.bookPublisher = bookPublisher;
        }