### @Data、@NoArgsConstructor和@AllArgsConstructor的使用
@Data:自动为所有字段添加@ToString, @EqualsAndHashCode, @Getter方法，为非final字段添加@Setter,和@RequiredArgsConstructor
@NoArgsConstructor: 自动生成无参数构造函数。 
@AllArgsConstructor: 自动生成全参数构造函数。 
用法如下

```java
@Data
@Builder
@NoArgsConstructor
@AllArgsConstructor
public class BaseBridge extends BaseEntity {}
```

