# Conectar-a-DB-con-java
codigo para conectar a una base de datos utilizando java
```
Requisitos: 
Tener instalado mysql.
Descargar el driver jdbc para mysql e implementar el archivo .jar al build path del proyecto.
```

```java
try {
	/*1. Conectamos a la base de datos
	PARA PONER LA ZONA HORARIA CORRESPONDIENTE A EUROPA EJECUTAMOS LA QUERY "SET GLOBAL time_zone = '-3:00';"
	*/
	Connection miConnection = DriverManager.getConnection("jdbc:mysql://localhost:3306/pruebas","root","");
	//2. Creamos objeto statment
	Statement miStatement = miConnection.createStatement();
	//3.ejecutar SQL
	ResultSet miResultset =  miStatement.executeQuery("SELECT * FROM corredores");
	//4. devolver el resultset
	while(miResultset.next()) {
		System.out.println(miResultset.getString("id") + " " + miResultset.getString("nombre"));
	}
}catch (SQLException e) {
	System.out.println("no chana nene");
	e.printStackTrace();
}

//metodo para insertar en la base de datos
	public static void insertarEnDB(String nombre) throws SQLException {
		Connection conexion = DriverManager.getConnection("jdbc:mysql://localhost:3306/pruebas","root","");
		Statement statement = conexion.createStatement();
		int insertar = statement.executeUpdate("insert into corredores values(null,"+ nombre + ")");
		conexion.close();
	}
//metodo para borrar campo en la base de datos
	public static void borrarEnDB(String nombre) throws SQLException {
		Connection conexion = DriverManager.getConnection("jdbc:mysql://localhost:3306/pruebas","root","");
		Statement statement = conexion.createStatement();
		int borrar = statement.executeUpdate("delete from corredores where nombre=" + nombre);	
	}
```
