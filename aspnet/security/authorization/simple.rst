.. _security-authorization-simple:

Simple Authorization
====================

Authorization is controlled through the Authorize attribute and its various parameters. At its simplest applying the Authorize attribute to a controller or action limits access to the controller or action to any authorized user.

For example, the following code limits access to the AccountController to any authorized user.

.. code-block:: c#

  [Authorize]
  public class AccountController : Controller
  {  
      public ActionResult Login()
      {      
      }

      public ActionResult Logout()
      {      
      }
  }

If you want to apply authorization to an action rather than the controller simply apply the Authorize attribute to the action itself;

.. code-block:: c#

  public class AccountController : Controller
  {  
      public ActionResult Login()
      {      
      }

      [Authorize]
      public ActionResult Logout()
      {      
      }
  }

Now only authenticated users can access the logout function.

You can also use the AllowAnonymous attribute to allow access by non-authenticated users to individual actions; for example the following usage will only allow authenticated users to the Account controller, except for the Login action, which is accessible by everyone, regardless of their authenticated or unauthenticated / anonymous status.

  [Authorize]
  public class AccountController : Controller
  {  
      [AllowAnonymous]
      public ActionResult Login()
      {      
      }

      public ActionResult Logout()
      {      
      }
  }
