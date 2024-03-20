### Hi there 👋

<!--
**phecdaDia/phecdaDia** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

-->
- 📫 How to reach me: Send me a quick github message or reach me by mail. 😉
- 😄 Pronouns: she/her
- ⚡ Fun fact: Did you know that you can calculate the modulo of two numbers $n$ and $d$ by doing modulo reductions by $b$, which you can simply set to a power of two. This allows you to calculate modulo with only bitshifting, additions and a multiplication. Anyways, here is an example:

```rust
fn fmod(n: u32, d: u32) -> u32 
{
	// Check if n is less than d first
	if n < d { return n; }
	
	// Find a suitable p for our base
	for p in 2..32 {
		if 1 << p > n { 
            // Will always find a p.
			return fmod_p(n, d, p)
		}
	}
	unreachable!(); // Mark as unreachable
}

fn fmod_p(n: u32, d: u32, p: u32) -> u32
{
	if n < 1 << p {
		if n < d { return n; }
		if n < d << 1 { return n - d; }
		return fmod_p(n, d, p-1);
	}
	
	fmod_p(
		((1 << p) - d) * (n >> p) + (n & ((1 << p) - 1)),
		d,
		p
	)
} 

fn main() {
	// Simple fizzbuzz example
	for i in 1..101 {
		let mut s = String::new();
		if fmod(i, 3) == 0 { s.push_str("Fizz"); }
		if fmod(i, 5) == 0 { s.push_str("Buzz"); }
		if s.is_empty() { s.push_str(&i.to_string()); }
		println!("{}", s);
	}
}
```

