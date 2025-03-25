//clase 1 
package RequerimientoFuncional;
public class empleados {
    private String nombre;
    private String cedula;
    private String departamento;
    private String tipoContrato;//temporal o permanente

    public empleados(String nombre, String cedula, String departamento, String tipoContrado) {
        this.nombre = nombre;
        this.cedula = cedula;
        this.departamento = departamento;
        this.tipoContrato=tipoContrato;
    }

    public String getNombre() {
        return nombre;
    }

    public void setNombre(String nombre) {
        this.nombre = nombre;
    }

    public String getCedula() {
        return cedula;
    }

    public void setCedula(String cedula) {
        this.cedula = cedula;
    }

    public String getDepartamento() {
        return departamento;
    }

    public void setDepartamento(String departamento) {
        this.departamento = departamento;
    }
    public String getTipoContrato(){
         return tipoContrato;
    }
    public void setTipoContrato(String tipoContrato){
         this.tipoContrato=tipoContrato;
    }
}

//clase 2
package RequerimientoFuncional;


public class newEmpleado {
    private static int contador=1;
    private int id;
    private String nombre;
    private String departamento;

    public newEmpleado(String nombre, String departamento) {
        this.nombre = nombre;
        this.departamento = departamento;
        this.id=contador;
        contador++;
    }

    public newEmpleado() {
        this.nombre="";
        this.departamento="";
        this.id=contador;
        contador++;
    }

    public String getNombre() {
        return nombre;
    }

    public void setNombre(String nombre) {
        this.nombre = nombre;
    }

    public String getDepartamento() {
        return departamento;
    }

    public void setDepartamenro(String departamento) {
        this.departamento = departamento;
    }

    public int getId() {
        return id;
    }
    @Override
    public String toString (){
        return"Producto "+id+"\n"+
        "nombre "+nombre+"\n"+
        "departamento "+departamento+"\n";
    } 
}
//clase3
package RequerimientoFuncional;
import java.util.ArrayList;

public class gestionEmpleados {
    private ArrayList<newEmpleado> newempleados;
    public gestionEmpleados (ArrayList<newEmpleado>newempleados){
        this.newempleados=newempleados;
    }
    public gestionEmpleados(){
        this.newempleados=newempleados;
    }

    public ArrayList<newEmpleado> getNewempelados() {
        return newempleados;
    }
    //metodo CRUD
    //agregar producto
    public boolean adicionarnewEmpelado(newEmpleado empleado){
        return this.newempleados.add(empleado);
    }
    //buscar producto
    public newEmpleado buscarNewEmpleado(newEmpleado empleado){
        for (int i=0; i < this.newempleados.size(); i++){
            newEmpleado p=this.newempleados.get(i);
            if (p.equals(empleado)){
                return p;
            }
        }
        return null;
    }
 
    public newEmpleado buscarNewEmpleado(long id){
        for (int i=0; i < this.newempleados.size(); i++){
            newEmpleado p=this.newempleados.get(i);
            if (p.getId()==id){
                return p;
            }
        }
        return null;
    }
    public newEmpleado buscarNewEmpleado(String nombre){
        for (int i=0; i < this.newempleados.size(); i++){
            newEmpleado p=this.newempleados.get(i);
            if (p.getNombre().equals(nombre)){
                return p;
            }
        }
        return null;
    }
    //modificar producto
    private int bucarIndiceEmpleado(long id){
        for (int i=0; i< newempleados.size(); i++){
            newEmpleado p = this.newempleados.get(i);
            if (p.getId()==id){
                return i;
            }
        }
        return -1;
    }
    public newEmpleado actualizarEmepleado(long id, newEmpleado newempleadoo){
        int index=this.bucarIndiceEmpleado(id);
        if (index>0){
            return this.newempleados.set(index, newempleadoo);
        }else{
            return null;
        }
    }
    //eliminar producto
    public newEmpleado eliminarempleado(long id){
        int index =this.bucarIndiceEmpleado(id);
        if (index>0){
            return this .newempleados. remove(index);
        }else{
            return null;
        }
    }
    //mostra inventario
    public String mostrarGestionEmpleados(){
        String gestionEmpleados="";
        for (int i=0; i< this.newempleados.size(); i++){
            newEmpleado p=this.newempleados.get(i);
            gestionEmpleados +=p.toString()+"\n";
            
        }
        return gestionEmpleados;
    }
}

//clase 4
package RequerimientoFuncional;


public class interfazUsuario {
    private String nombre;
    private String departamento;
    private Administrador admin;
    private gestionEmpleados gestEmp;

    public interfazUsuario(String nombre, String departamento) {
        this.nombre = nombre;
        this.departamento = departamento;
    }

    public void setAdmin(Administrador admin) {
        this.admin = admin;
    }
    
    

    public String getNombre() {
        return nombre;
    }

    public void setNombre(String nombre) {
        this.nombre = nombre;
    }

    public String getDepartamento() {
        return departamento;
    }

    public void setDireccion(String departamento) {
        this.departamento = departamento;
    }
    //metodo de gestion
    public boolean agregarEmpleado(newEmpleado newempleadoo){
        return this.gestionEmpleados.adicionarnewEmpleado(newempleadoo);
        
    }
     public newEmpleado buscarEmpleado(newEmpleado newempleadoo){
        return this.gestionEmpleados.buscarEmpleado(newempleadoo);
        
    }
    public newEmpleado buscarEmpleado(long id){
        return this.gestionEmpleados.buscarempleado(id);
    }
     public newEmpleado actualizarEmpleado(long id, newEmpleado newempleadoo){
        return this.gestionEmpleados.actualizarEmpleado(id, newempleadoo);
    }
    public newEmpleado eliminarEmpleado(long id){
        return this.gestionEmpleado.buscarEmpleado(id);
    }
    public String mostrarGEstionEmpleado(){
        return this.gestionEmpleado.mostrarGestionEmpleado();
    }
    public boolean iniciarSesion(String user, String pass ){
        return user.equals(this.admin.getUserName())&& pass.equals(this.admin.getPassword());
    }
}
//clase 5
package RequerimientoFuncional;


public class Administrador extends empleados{
    private String userName;
    private String password;

    public Administrador(String userName, String password, String nombre, String cedula, String departamento, String tipoContrato) {
        super(nombre, cedula, departamento, tipoContrato);
        this.userName = userName;
        this.password = password;
    }

    public String getUserName() {
        return userName;
    }

    public void setUserName(String userName) {
        this.userName = userName;
    }

    public String getPassword() {
        return password;
    }

    public void setPassword(String password) {
        this.password = password;
    }
}



