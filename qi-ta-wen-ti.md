# 其他问题

### 1、报错：Cannot reduce the visibility of the inherited method from

原因：子类方法的访问权限低于基类该方法的访问权限。

解决办法：调整子类方法的访问权限大于或等于基类的访问权限。

解释：如果允许子类方法降低父类方法的权限，当通过父类引用调用子类方法时，将掩盖掉该错误（子类方法访问权限较低）。这种思想将引起大量错误的出现。举个例子，父类A中有protected void show\(\)，子类重写时不能将protected修改为public，只能改为private或不改。

