# 400 Obfuscript

> For too long the Nyan cats have been held captive in the Mellsogg's factories where they have undergone genetic experimentation (you can see results of these experiments here). EATA, Everyone Attempting to free Tasty Animals, has uncovered Mellsogg's control panel during their investigation into Mellsogg's illegal experimentation and hopes that you will be able to finally set free these delicate pastries.
>
> If you find a solution and the site says it is right, but it is actually wrong, try finding another solution.
>
> http://54.86.217.7/

The page shows a strange set of buttons. Since it's called Obfuscript, let's look at the JS source code first. The obfuscated code is inside [challenge.js](http://54.86.217.7/challenge.js).

The first thing I did was stick this code inside [JSBeautifier](http://jsbeautifier.org) to see what it did. After simplifying it, the function `updateKey()` was particularly noteworthy.

```javascript
function updateKey(_0xa3edxc, _0xa3edxd) {
	switch (_0xa3edxc) {
		case (0):
			keyString = _0xa3edxd;
			us[_0x6cab[33]] = _0xa3edxd;
			break;;
		case (1):
			keyNumber = Math[_0x6cab[19]](parseInt(_0xa3edxd));
			un[_0x6cab[33]] = ([] + []) + Math[_0x6cab[19]](parseInt(_0xa3edxd));
			break;;
		case (2):
			keyBool = _0xa3edxd;
			ub[_0x6cab[33]] = ([] + []) + _0xa3edxd;
			break;;
	};
	(keyString == (([] + []) + (([] + {})[1] && true) + typeof({} + {}))[_0x6cab[41]](-12, -4) + (++[
		[]
	][+[]] + [+[]]) + ([] + {}[1])[4] + (typeof(NaN))[5] + (Array(2 << 3)[_0x6cab[28]](_0x6cab[42])[_0x6cab[15]] - 11) + ~[] * ((((+((([] + {})[_0x6cab[46]](_0x6cab[49], _0x6cab[50])[_0x6cab[46]](_0x6cab[47], _0x6cab[48])[_0x6cab[46]](_0x6cab[45], _0x6cab[0])[_0x6cab[17]](_0x6cab[44])[_0x6cab[43]]()[0][0]) + 5) - 13) << 6) + ~[]) >> 2)) ? ((keyNumber % ([_0x6cab[52], _0x6cab[52], _0x6cab[52], _0x6cab[52]][_0x6cab[51]](parseInt)[2]) == 0) && (keyNumber % (Array(9)[_0x6cab[28]](_0x6cab[42])[_0x6cab[15]]) == parseInt(1 / 0, 19)) && (keyNumber > parseInt(_0x6cab[53], 10)) && (~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~keyNumber & 69 | ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~69 & keyNumber) && (keyNumber < Array(20)[_0x6cab[28]]([] + {})[_0x6cab[15]])) ? (keyBool == (([0] == ![0] && NaN === NaN && (null instanceof Object)) || ((_0x6cab[54] instanceof String) == (true + false == 1)) && (!!(_0x6cab[55])))) ? right(): wrong(): wrong(): wrong();
}
```

It seems that if the long string of conditions are satisfied, then the page will congratulate you. Let's take a closer look at these conditions.

```javascript
(keyString == (([] + []) + (([] + {})[1] && true) + typeof({} + {}))[_0x6cab[41]](-12, -4) + (++[[]][+[]] + [+[]]) + ([] + {}[1])[4] + (typeof(NaN))[5] + (Array(2 << 3)[_0x6cab[28]](_0x6cab[42])[_0x6cab[15]] - 11) + ~[] * ((((+((([] + {})[_0x6cab[46]](_0x6cab[49], _0x6cab[50])[_0x6cab[46]](_0x6cab[47], _0x6cab[48])[_0x6cab[46]](_0x6cab[45], _0x6cab[0])[_0x6cab[17]](_0x6cab[44])[_0x6cab[43]]()[0][0]) + 5) - 13) << 6) + ~[]) >> 2))
	? ((keyNumber % ([_0x6cab[52], _0x6cab[52], _0x6cab[52], _0x6cab[52]][_0x6cab[51]](parseInt)[2]) == 0) && (keyNumber % (Array(9)[_0x6cab[28]](_0x6cab[42])[_0x6cab[15]]) == parseInt(1 / 0, 19)) && (keyNumber > parseInt(_0x6cab[53], 10)) && (~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~keyNumber & 69 | ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~69 & keyNumber) && (keyNumber < Array(20)[_0x6cab[28]]([] + {})[_0x6cab[15]]))
		? (keyBool == (([0] == ![0] && NaN === NaN && (null instanceof Object)) || ((_0x6cab[54] instanceof String) == (true + false == 1)) && (!!(_0x6cab[55]))))
			? right()
		: wrong()
	: wrong()
: wrong();
```

So there's 3 conditions, one on each of `keyString`, `keyNumber`, and `keyBool`. The conditions are long, but most of it can be evaluated immediately. I used the JavaScript console inside Google Chrome to evaluate it.

We know that `keyString` must equal `(([] + []) + (([] + {})[1] && true) + typeof({} + {}))[_0x6cab[41]](-12, -4) + (++[[]][+[]] + [+[]]) + ([] + {}[1])[4] + (typeof(NaN))[5] + (Array(2 << 3)[_0x6cab[28]](_0x6cab[42])[_0x6cab[15]] - 11) + ~[] * ((((+((([] + {})[_0x6cab[46]](_0x6cab[49], _0x6cab[50])[_0x6cab[46]](_0x6cab[47], _0x6cab[48])[_0x6cab[46]](_0x6cab[45], _0x6cab[0])[_0x6cab[17]](_0x6cab[44])[_0x6cab[43]]()[0][0]) + 5) - 13) << 6) + ~[]) >> 2)`. Although this looks really complicated, if you evaluate this in the JavaScript console on the page, you'll realize that it's equivalent to `"truest10fr34-511"`.

`keyNumber` has several more conditions. First of all, it must be divisible by `([_0x6cab[52], _0x6cab[52], _0x6cab[52], _0x6cab[52]][_0x6cab[51]](parseInt)[2])`, which, if we use the console again, evaluates to 2. Also, `keyNumber` `%` `(Array(9)[_0x6cab[28]](_0x6cab[42])[_0x6cab[15]])` must equal `parseInt(1 / 0, 19)`. Using the console again, we know that `keyNumber` must be equivalent to 18 mod 24. The third condition simply states that `keyNumber` must be greater than 0. In the fourth condition, there are many tildes (`~`), but you should know that two tildes gives you the original number. There are an odd number of tildes, so the expression simplifies to `~keyNumber & 69 | ~69 & keyNumber`. The final condition says that `keyNumber` must be less than 285.

Here's a summary of the conditions on `keyNumber`:

- `keyNumber` is even.
- `keyNumber` is equivalent to 18 mod 24.
- `~keyNumber & 69 | ~69 & keyNumber` must return true. This condition doesn't really make sense, as you will see that every number that satisfies other conditions also satisfies this one.
- `keyNumber` is between 0 and 285.

Based on the previous conditions, the list of numbers that works is `[18, 42, 66, 90, 114, 138, 162, 186, 210, 234, 258, 282]`.