## Unit Test in Java

1. Create MathService class
2. Create a method sum()

3. Create a unit test for this method.

Hi, I want to be able to get a sum of 2 numbers, but if the sum is above 100, then I want to receive 0 instead.

```java
package com.datorium.Datorium.API;

public class MathService {
    //Create a method sum()
    public int sum(int a, int b) {
        int sum = a + b;
        if (sum > 100) {
            return 0;
        }
        return sum;
    }
}
```

```java
package com.datorium.Datorium.API;

import org.junit.jupiter.api.Test;
import static org.assertj.core.api.Assertions.assertThat;


public class MathServiceTest {
    //Hi, I want to be able to get a sum of 2 numbers, but if the sum is above 100, then I want to receive 0 instead.
    @Test
    public void WHEN_SumIsGreaterThan100_THEN_Result_IsZero() {
        var mathService = new MathService();
        assertThat(mathService.sum(55, 80)).isEqualTo(0);
    }

    @Test
    public void WHEN_SumIsSmallerThan100_THEN_Result_IsSum() {
        var mathService = new MathService();
        assertThat(mathService.sum(63, 36)).isEqualTo(99);
    }

    @Test
    public void WHEN_SumIs100_THEN_Result_IsSum() {
        var mathService = new MathService();
        assertThat(mathService.sum(63, 37)).isEqualTo(100);
    }

}
```
