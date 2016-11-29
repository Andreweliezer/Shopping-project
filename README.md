# Shopping-project

using System;
using System.Collections.Generic;
using System.Linq;
using System.Web;
using System.Web.Mvc;
using ADO.Models;

namespace ADO.Controllers
{
    public class HomeController : Controller
    {
        DataContext db = new DataContext();
        public ActionResult Index()
        {
            List<Employee> emplst = db.getEmployees();
            return View(emplst);
        }

        public ActionResult Details(int id)
        {
            Employee obj = db.getEmployee(id);
            return View(obj);
        }

        [HttpGet]
        public ActionResult Delete(int id)
        {
            Employee obj = db.getEmployee(id);
            return View(obj);
        }

        [HttpPost]
        [ActionName("Delete")]
        public ActionResult DeleteConfirm(int id)
        {
            db.DeleteEmp(id);            
            return RedirectToAction("Index");
        }

        [HttpGet]
        public ActionResult Edit(int id)
        {
            Employee obj = db.getEmployee(id);
            return View(obj);
        }

        [HttpPost]
        public ActionResult Edit(Employee obj)
        {
            db.EditEmp(obj);
            return RedirectToAction("Index");
        }
    }
}
