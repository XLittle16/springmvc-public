shiro框架 
SecurityUtils.getSubject()
=
   public static Subject getSubject() {
        Subject subject = ThreadContext.getSubject();
        if (subject == null) {
            subject = (new Subject.Builder()).buildSubject();
            ThreadContext.bind(subject);
        }
        return subject;
    }

ThreadContext 使用了Shiro把Subject和当前线程关联起来，方便获取。但是为什么要使用InheritableThreadLocalMap，这个可以获取到父线程的（就是依附的那个线程）ThreadLocalMap
