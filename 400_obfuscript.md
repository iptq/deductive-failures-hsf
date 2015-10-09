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