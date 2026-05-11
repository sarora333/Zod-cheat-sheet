# Zod Validation Cheat Sheet

## String Validations
- `.min(length, message?)` — Minimum string length  
- `.max(length, message?)` — Maximum string length  
- `.length(exactLength, message?)` — Exact string length  
- `.email(message?)` — Valid email format  
- `.url(message?)` — Valid URL format  
- `.uuid(message?)` — Valid UUID format  
- `.regex(regex, message?)` — Regex pattern match  
- `.nonempty(message?)` — Not empty string  
- `.startsWith(str, message?)` — Starts with substring  
- `.endsWith(str, message?)` — Ends with substring  
- `.trim()` — Trim whitespace before validation  

## Number Validations
- `.min(value, message?)` — Minimum number value  
- `.max(value, message?)` — Maximum number value  
- `.int(message?)` — Must be integer  
- `.positive(message?)` — Must be > 0  
- `.negative(message?)` — Must be < 0  
- `.nonnegative(message?)` — Must be ≥ 0  
- `.nonpositive(message?)` — Must be ≤ 0  
- `.finite(message?)` — Must be finite (no Infinity or NaN)  

## Array Validations
- `.min(length, message?)` — Minimum array length  
- `.max(length, message?)` — Maximum array length  
- `.length(exactLength, message?)` — Exact array length  
- `.nonempty(message?)` — Array not empty  
- `.unique(comparator?, message?)` — Unique elements  

## Object Validations
- `.partial()` — Make all keys optional  
- `.required()` — Make keys required  
- `.strict()` — No unknown keys allowed  
- `.passthrough()` — Allow unknown keys  

## Common Methods
- `.optional()` — Field can be undefined  
- `.nullable()` — Field can be null  
- `.default(value)` — Default value if undefined  
- `.refine(predicate, { message })` — Custom validation  
- `.transform(transformFn)` — Transform input  
- `.catch(defaultValue)` — Fallback value on failure  

---

## Example Schema

```ts
import { z } from "zod";

const userSchema = z.object({
  username: z.string().min(3).max(15),
  email: z.string().email(),
  age: z.number().int().min(18).max(65).optional(),
  tags: z.array(z.string()).max(10).optional(),
});
