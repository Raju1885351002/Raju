// Creating the table

create table Movies(Movie_Name varchar(20),Actor_Name varchar(20),Actress_Name varchar(20),Year_of_release int(4),Director_Name varchar(20));

// Inserting the values 

insert into Movies values("Gabbarsingh","PavanKalyan","Shruthi Haasan",2012,"Harish Shankar");
insert into Movies values("Bhahubali","Prabhas","Anushka",2015,"S.S.Rajamouli");
insert into Movies values("MCA","Nani","Sai Pallavi",2017,"Venu SriRam");
insert into Movies values("Geetha Govindam","Vijay Devarakonda","Rashmika Mandanna",2018,"Parasuram");
insert into Movies values("Uppena","Vaishnav Tej","Krithi Shetti",2021,"Buchi Babu Sana");

// Select the data

Select * from Movies;

Gabbarsingh|PavanKalyan|Shruthi Haasan|2012|Harish Shankar
Bhahubali|Prabhas|Anushka|2015|S.S.Rajamouli
MCA|Nani|Sai Pallavi|2017|Venu SriRam
Geetha Govindam|Vijay Devarakonda|Rashmika Mandanna|2018|Parasuram
Uppena|Vaishnav Tej|Krithi Shetti|2021|Buchi Babu Sana









import java.sql.Connection;  
import java.sql.DriverManager;  
import java.sql.PreparedStatement;  
import java.sql.SQLException;  
   
public class InsertRecords {  
   
    private Connection connect() {  
        String url = "jdbc:sqlite:C://sqlite/SSSIT.db";  
        Connection conn = null;  
        try {  
            conn = DriverManager.getConnection(url);  
        } catch (SQLException e) {  
            System.out.println(e.getMessage());  
        }  
        return conn;  
    }  
   
  
    public void insert(String Movie_Name,String Actor_Name,String Actress_Name,double Year_of_release,String Director_name) {  
        String sql = "INSERT INTO Movies(Movie_Name, Actor_Name,Actress_Name,Year_of_release,Director_name) VALUES(?,?,?,?,?)";  
   
        try{  
            Connection conn = this.connect();  
            PreparedStatement pstmt = conn.prepareStatement(sql);  
            pstmt.setString(1, Movie_Name);  
            pstmt.setString(2, Actor_Name);
            pstmt.setString(3, Actress_Name);
            pstmt.setInteger(4, Year_of_release);
            pstmt.setString(5, Director_name);
            pstmt.executeUpdate();  
        } catch (SQLException e) {  
            System.out.println(e.getMessage());  
        }  
    }  
   
    public static void main(String[] args) {  
   
        InsertRecords app = new InsertRecords();   
        app.insert("Gabbarsingh","PavanKalyan","Shruthi Haasan",2012,"Harish Shankar");  
        app.insert("Bhahubali","Prabhas","Anushka",2015,"S.S.Rajamouli");  
        app.insert("MCA","Nani","Sai Pallavi",2017,"Venu SriRam");
        app.insert("Geetha Govindam","Vijay Devarakonda","Rashmika Mandanna",2018,"Parasuram");
        app.insert("Uppena","Vaishnav Tej","Krithi Shetti",2021,"Buchi Babu Sana");
    }  
   
}  
























