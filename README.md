# My stuff

Hi, I write programs (and often, programming languages). Mainly, the...

## Maverick Programming Language

At the time of writing, I have not made this public. However, it looks like this:

```pascal
program BumpTest;

uses BumpAllocator;
uses Console;

function Main(args: string*, count: int32): int32; begin
	var bump := BumpAllocator::Create(1kb);

	if !bump then
	begin
		Console::PrintLn('Cannot create bump allocator');
		return -1;
	end;

	var arr := heaparray[type int32*, 256];

	for var i := 0; i < 256; i += 1 do begin
		var ptr: int32* := bump.Alloc(size type int32);
		*ptr := 200 + i;
		arr[i] := ptr;
	end;

	for var i := 0; i < 256; i += 1 do begin
		Console::PrintInt(*arr[i]);
		Console::PrintLn('');
	end;

	Console::PrintLn('If we haven\'t segfaulted, then the bump allocator works!');

	bump.Destroy();
	Mem::Free(arr);

	return 0;
end;
```

I promise it's not just a Pascal clone with manual memory—it has its own distinct features as well. Have you ever heard of a:

- `MemoryContext`
- `match` (okay probably this one)
- Standard library that only gets compiled to the extent that it is used
- Pascal-like language that makes you look really cool?

No? Well, now you have! Stay tuned.
