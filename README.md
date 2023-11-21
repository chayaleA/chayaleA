using Microsoft.AspNetCore.Identity;
using Microsoft.AspNetCore.Mvc;
using System.ComponentModel.DataAnnotations;

// For more information on enabling Web API for empty projects, visit https://go.microsoft.com/fwlink/?LinkID=397860

namespace bank_api_project.Controllers
{
    [Route("api/[controller]")]
    [ApiController]
    public class OfficialBankController : ControllerBase
    {
        public static List<OfficialBank> listOfficials = new List<OfficialBank>
        {
            new OfficialBank{Name = "Yael",Id = 123456789, Phone = 0583238801, Role = Degree.Withrawal,Salary = 100},
            new OfficialBank{Name = "Yael",Id = 123456789, Phone = 0583238801, Role = Degree.Withrawal,Salary = 100},
            new OfficialBank{Name = "Yael",Id = 123456789, Phone = 0583238801, Role = Degree.Withrawal,Salary = 100},
            new OfficialBank{Name = "Yael",Id = 123456789, Phone = 0583238801, Role = Degree.Withrawal,Salary = 100}
        };

        [HttpGet]
        public IEnumerable<OfficialBank> Get()
        {
            return listOfficials;
        }

        [HttpGet("{id}")]
        public ActionResult<OfficialBank> Get(int id = 0, string? name = "", int? phone = 0 , Degree? role = 0)
        {
            OfficialBank temp = listOfficials.Find(e => e.Id == id);
            if (temp == null)
                return NotFound();
            return temp;
        }

        //[HttpGet("{id}/name")]
        //public ActionResult<OfficialBank>  Get(int id, [FromBody] string name)
        //{
        //    var l = listOfficials.Find(g => g.Name.Equals(name));
        //    if (l == null)
        //        return NotFound();
        //    else
        //        return l;
        //}

        [HttpPost]
        public void Post([FromBody] OfficialBank value)
        {
            listOfficials.Add(value);
        }


        [HttpPut("{id}")]
        public void Put(int id, [FromBody] OfficialBank value)
        {
            OfficialBank temp = listOfficials.Find(e => e.Id == id);
            if (temp == null)
            {
                listOfficials.Add(value);
                return;
            }
            temp.Id = id;
            temp.Name = value.Name;
            temp.Salary = value.Salary;
            temp.Role = value.Role;
            temp.Phone = value.Phone;
            listOfficials.Add(temp);
        }

        [HttpDelete("{id}")]
        public void Delete(int id)
        {
            OfficialBank temp = listOfficials.Find(e => e.Id == id);
            if (temp != null)
                listOfficials.Remove(temp);
        }
    }
}

<!---
chayaleA/chayaleA is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
