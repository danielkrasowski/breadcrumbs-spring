<i>breadcrumbs-spring.jar</i> is library dedicated for Spring MVC. This library based on annotation and interceptor. Additionally annotation includes few attributes, which allow for some customization:

<b>Label</b> - Display label for the link. You can define static text or key of element at property file.<br>
<b>Parent</b> – define parent of current localization. Parent with empty value indicate that it is root of user position.<br>
<b>Message</b> - Attribute allow only Boolean type and it indicate that definition of bread crumbs based on message properties, including right localization.<br>
<b>Dynamic</b> – Attribute allow only Boolean type and it indicate that, the label can be sat dynamically from method. Only what you mas too do, use instance of <i>Model</i> and label by <i>model.addAttribute(“breadLabel”, “Welcome”);</i><br>
