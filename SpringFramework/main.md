容器启动                                                  + 代表容器级生命周期方法
                                                          = 代表Bean自身方法
+调用BeanFactoryPostProcessor                             - 代表Bean级生命周期方法
 #postProcessBeafactory方法

通过getBean()调用某一个Bean

 +调用instantiationAwareBeanPostProcessor                                               1. 实例化
  #postProcessBeforeInstantiation()方法

=实例化Bean

+调用instantiationAwareBeanPostProcessor
 #postProcessAfterinstantiation()方法
---------------------------------------------------------------------------------------------------------
+调用instantiationAwareBeanPostProcessor
 #postProcessPropertyValues()方法
 
 =设置Bean的属性值
 
 -检查Aware的相关接口并设置相关依赖    -调用BeanNameAware#setBeanName()方法
                                    -调用BeanClassLoaderAware#setBeanClaLoader()方法
                                    -调用BeanFactoryAware#setBeanFactory()方法                         2. 属性赋值
                                    -调用EnvironmentAware#setEnvironment()方法
                                    -调用ResourceLoaderAware#serResourceLoader()方法
                                    -调用ApplicationEventPublisherAware#setApplicationEventPublisher()方法
                                    -调用MessageSourceAware#setMessageSource()方法
                                    -调用ApplicationContextAware#setApplicationContext()方法
-----------------------------------------------------------------------------------------------------------                                    
+调用BeanPostProcessor
 #postProcessBeforeInitialization()方法
 
 =调用@PostConstruct标注的自定义初始化方法
                                                                             3. 初始化
 -调用initializingBean#afterPropertiesSet()方法
 
 =调用init-method配置的自定初始化方法
 
 +调用BeanPostPrecessor#postPrecessAfterInitialization()方法
 ------------------------------------------------------------------------------------------------------------
(该Bean作用域为 singleton)                          该Bean作用域为Prototype

Spring缓存池中准备就绪的Bean                         将准备就绪的Bean交给调用者, 剩下的生命周期有用户控制              使用中

Bean使用中

------------------------------------------------------------------------------------------------------------
(容器销毁)

=调用@PreDestroy标注的自定义销毁方法

-调用DisposableBean#destroy()方法                        4 销毁

=调用destory-method配置的自定义销毁方法

(结束)








