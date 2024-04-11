
using System.Data;
using System.Data.SqlClient;
using System.Data.SqlTypes;
using static System.Runtime.InteropServices.JavaScript.JSType;

Console.WriteLine("Hello, World!");

//F10 

SqlConnectionStringBuilder stringBuilder = new SqlConnectionStringBuilder();
stringBuilder.DataSource = "AGD-PC-535";
stringBuilder.InitialCatalog = "DotNetTraningBath4";
stringBuilder.UserID = "sa";
stringBuilder.Password = "sa@123";

SqlConnection connection = new SqlConnection (stringBuilder.ConnectionString);

//SqlConnection connection = new SqlConnection("Data Source = AGD - PC - 535; Initial Catalog = DotNetTraningBath4; User ID = sa; Password = sa@123");
connection.Open();

string query = "select * from Tbl_Blg";
SqlCommand cmd = new SqlCommand(query, connection);
SqlDataAdapter SqlDataAdapter = new SqlDataAdapter(cmd);
DataTable dt = new DataTable();
SqlDataAdapter.Fill(dt);

connection.Close();

//dataset -> DataTable
//DataTable -> datarow
//datawor -> datacolunm

foreach(DataRow dr in dt.Rows)
{
    Console.WriteLine("Blog ID" + dr["BlogID"]); 
    Console.WriteLine("Blog Title" + dr["BlogTitle"]);
    Console.WriteLine("Blog Author" + dr["BlogAuthor"]);
    Console.WriteLine("Blog Content" + dr["BlogContent"]);
    Console.WriteLine("----------------------");
}

Console.ReadKey();

