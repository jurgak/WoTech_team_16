We tried to use Enum class for bigger, smaller and equals
```java
Enum class

package com.datorium.Datorium.API;

public enum GuessResult {
    Bigger,
    Smaller,
    Equals
}
```
``` java
NumberGame class

package com.datorium.Datorium.API;

public class NumberGame {
    public int randomNumber;

    public void setRandomNumber(int randomNumber) {
        this.randomNumber = randomNumber;

    }
    public GuessResult guessANumber(int guess) {
        if(guess > randomNumber) {
            return GuessResult.Bigger; //too big
        } else if(guess < randomNumber) {
            return GuessResult.Smaller; // too small
        } else {
            return GuessResult.Equals; // correct answer
        }
    }
}
```
```java
Tests class

import org.springframework.util.Assert;

public class NumberGameTests {
    @Test
    public void WHEN_GuessIsTooBig_THEN_return_Bigger() {
        var game = new NumberGame();
        game.setRandomNumber(15);
        var response = game.guessANumber(26);
        Assert.isTrue(response == GuessResult.Bigger, "Result supposed to be Bigger");
    }
    @Test
    public void WHEN_GuessIsTooSmall_THEN_return_Smaller() {
        var game = new NumberGame();
        game.setRandomNumber(23);
        var response = game.guessANumber(10);
        Assert.isTrue(response == GuessResult.Smaller, "Result supposed to be Smaller");
    }
    @Test
    public void WHEN_GuessIsCorrect_THEN_return_Equals() {
        var game = new NumberGame();
        game.setRandomNumber(5);
        var response = game.guessANumber(5);
        Assert.isTrue(response == GuessResult.Equals, "Result supposed to be Equals");
    }

}
```
