# Sundries
****
**SpringConfig.xml解析，当遇到自定义标签会从表头获取解析类，根据相关格式进行解析**

**BeanDefinitionParserDelegate**
![image](image/parseCustomElement.png)

```java
   public class NamespaceHandler extends NamespaceHandlerSupport {
	 @Override
	 public void init() {
		 // 注册解析器
		 registerBeanDefinitionParser(ElementNames.RAMCACHE, new CustomParser());
	 }
   }
```
**解析流程**
   ![image](image/parseElement.png)
   
```java
      CustomParser extends AbstractBeanDefinitionParser{
        @Override
        protected AbstractBeanDefinition parseInternal(Element element, ParserContext parserContext) {
        }
      }
```

**添加CustomInstantiationAwareBeanPostProcessorAdapter**
```java
class PostProcessorRegistrationDelegate {
   public static void registerBeanPostProcessors(
		ConfigurableListableBeanFactory beanFactory, AbstractApplicationContext applicationContext) {
		......
		// Now, register all regular BeanPostProcessors.
		List<BeanPostProcessor> nonOrderedPostProcessors = new ArrayList<BeanPostProcessor>();
		for (String ppName : nonOrderedPostProcessorNames) {
	             BeanPostProcessor pp = beanFactory.getBean(ppName, BeanPostProcessor.class);
		     nonOrderedPostProcessors.add(pp);
		     if (pp instanceof MergedBeanDefinitionPostProcessor) {
		         internalPostProcessors.add(pp);
		     }
		}
		......
	}
    }
```
