# permitive types;
- i8~i128, isize
- u8~u128, usize
- f16, f32, f64
- bool

# composition types
- error
- struct
- union
- enum
- tuple
- array

# compile-time types
- integer, real, bool
- compile-time list
- compile-time map

# reference types
- const/mut pointer
- const/mut multi-pointer
- const/mut ref
- const/mut slice

# function types

# smid types

# stack frame types

# other types
- noreturn
- void
- user definition
- optional
- opaque
- anyopaue

# generic type
-- Something[T, N, F]
const Something = enum {
    a[T](T, T),
    b[N](N, N, N, N),
    c[F](F),
    d(usize),
    none,
};

-- SomeStruct[T]
const SomeStruct = struct {
    `generic T`
    name: ^AsStr,
    id: usize, 
    data: T,
};

const AsStr = trait {
    fn asStr(&self) []u8,
};

-- trait object of AsStr
-- ^AsStr {
--      self: *mut anytype, -- to the actual object
--      vtable: *anytype,   -- to the vtatble
-- }

-- ToString
const ToString = trait {
    fn toString(&self) String,
};


const A = struct {
    `derive Debug, Display`
    a: usize 
    b: usize,
};











