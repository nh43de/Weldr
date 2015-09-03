# Weldr

Weldr is a extensible Roslyn-based Visual Studio extension that makes it easy to manage and generate code during design time. Some example uses include controller method proxy generation, typescript interface generation from classes, and database-driven POCO objects.


**Controller Proxy Generation**

      namespace Namespace.Services {
          [WeldrExport(Weldr.CSProxy)]
          public class ExampleServices {
              public static ApiResult GetStuff(Context cx, int a, int b) {
                  var c = a + b;
      
                  return Ok(cx, c);
              }
          }
      }
      
      namespace Namespace.Proxies { 
          [WeldrImport(Weldr.CSProxy, "Namespace.Services.GetStuff")]
          public class ExampleServicesProxy {
            //proxy methods
          }
      }
      
**TypeScript Interface Generation**

      [WeldrExport(Weldr.TypeScript, "~\ViewScripts")]
      public class SimpleDTO {
          public string Name;
          public string Address;
          public DateTime SubmitDate;
      }
      
      File: ViewScripts\SimpleDTO.ts
      interface SimpleDTO {
          Name: string;
          Address: string;
          SubmitDate: Date;
      }
      
**Database-Driven POCO Objects**

      [WeldrImport(Weldr.DB, "dbo.Customers")]
      public class Customers
      {
            //database-driven code output here
      }
