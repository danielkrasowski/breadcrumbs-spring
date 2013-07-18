<i>breadcrumbs-spring.jar</i> is library dedicated for Spring MVC. This library based on annotation and interceptor. Additionally annotation includes few attributes, which allow for some customization:

<b>Label</b> - Display label for the link. You can define static text or key of element at property file.<br>
<b>Parent</b> – define parent of current localization. Parent with empty value indicate that it is root of user position.<br>
<b>Message</b> - Attribute allow only Boolean type and it indicate that definition of bread crumbs based on message properties, including right localization.<br>
<b>Dynamic</b> – Attribute allow only Boolean type and it indicate that, the label can be sat dynamically from method. Only what you mas too do, use instance of <i>Model</i> and label by <i>model.addAttribute(“breadLabel”, “Welcome”);</i><br>

-----------------------------------------------------

<b>Examples 1:</b>
Static text of label
```java
@Bread(label="Welcome", parent="")
@RequestMapping(value="/page", method=RequestMethod.GET)
public String getCandidate(Model model) {

  	return "page";
}
```

<b>Examples 2:</b>
Label loaded from message properties file
```java
@Bread(label="welcome.editTitle", parent="w1", message=true)
@RequestMapping(value="/page", method=RequestMethod.GET)
public String getCandidate(Model model) {

		return "page";
}
```

<b>Examples 3:</b>
Dynamic setting of label
```java
@Bread(parent="w2", dynamic=true)
@RequestMapping(value="/page", method=RequestMethod.GET)
public String getCandidate(Model model) {

  	
		model.addAttribute("breadLabel", "Welcome");
		
		return "page";
}
```
