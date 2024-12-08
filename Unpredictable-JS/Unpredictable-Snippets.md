### **Example 1: Adding Arrays**
```javascript
console.log([] + []);
```
**Output:**
```
""
```

**Explanation:**
- When `+` is used with arrays, JavaScript converts them to strings. Since both arrays are empty, their string representation is `""`, resulting in an empty string.

---

### **Example 2: Adding an Array and a Number**
```javascript
console.log([] + 1);
```
**Output:**
```
"1"
```

**Explanation:**
- The empty array is converted to an empty string (`""`), and `1` is then concatenated as a string. The result is `"1"`.

---

### **Example 3: Subtracting Arrays**
```javascript
console.log([] - []);
```
**Output:**
```
0
```

**Explanation:**
- The `-` operator does not perform string concatenation; it attempts to coerce both arrays into numbers. Both arrays are coerced into `0`, so the result is `0`.

---

### **Example 4: `null` vs `undefined` in Equality**
```javascript
console.log(null == undefined);  // true
console.log(null === undefined); // false
```

**Explanation:**
- `null` and `undefined` are loosely equal (`==`) because they both represent "no value."
- Strict equality (`===`) checks both type and value, so `null` and `undefined` are not strictly equal.

---

### **Example 5: Implicit Boolean Conversion**
```javascript
console.log([] == true);  // false
console.log([] == false); // true
```

**Explanation:**
- `[]` is truthy in a boolean context, but during loose equality (`==`) comparison, it's coerced into a string (`""`) which is falsy. Thus, `[] == false` is `true`.

---

### **Example 6: NaN Comparisons**
```javascript
console.log(NaN == NaN);  // false
console.log(Object.is(NaN, NaN)); // true
```

**Explanation:**
- `NaN` (Not-a-Number) is not equal to itself. This behavior is defined by IEEE 754 floating-point standards.
- Use `Object.is` to check strict equality for `NaN`.

---

### **Example 7: Misleading Type Coercion**
```javascript
console.log('5' - 3);  // 2
console.log('5' + 3);  // "53"
```

**Explanation:**
- `-` triggers numeric conversion, so `'5'` becomes `5`, and the result is `2`.
- `+` triggers string concatenation when one operand is a string, so `3` is converted to `"3"`, and the result is `"53"`.

---

### **Example 8: Comparing Objects**
```javascript
console.log({} + []); // "[object Object]"
console.log([] + {}); // "[object Object]"
```

**Explanation:**
- The `{}` object is converted to its string representation, `"[object Object]"`.
- Similarly, the empty array `[]` is converted to an empty string, and concatenation occurs.

---

### **Example 9: Array Holes**
```javascript
const arr = [1, , 3];
console.log(arr.length); // 3
console.log(arr[1]);     // undefined
```

**Explanation:**
- Creating an array with a hole (missing element) still allocates the index but leaves it undefined.

---

### **Example 10: Double Negation Quirk**
```javascript
console.log(![]);  // false
console.log(!![]); // true
```

**Explanation:**
- `[]` is truthy, so `![]` is `false`. Double negation (`!!`) converts the truthy value back to `true`.

---
