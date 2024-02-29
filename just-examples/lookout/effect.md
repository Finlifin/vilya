# No catching, no error, no more effect, single-element effect set, ask effect single time
pub fn main() !void {
    helloEffect()# {
        Some(data) => { println(data); true }
    }
}

effect Some(^Display) bool;

fn helloEffect() Some#void {
    if Some("Give me a bool.").perform {
        println("It's true");
    } else {
        println("It's false");
    }
}


main.-2-18Handler-main.Some {
    -- no catched field
    fn handle(data: []u8) bool {
        println(data);
        true
    }
}






# No catching, no error, no more effect, multi-element effect set, ask effect single time
pub fn main() !void {
    helloEffect()# {
        Some(data) => { println(data); true },
        WhatToSay => "Whatever you what to say",
    }
}

effect Some(^Display) bool;
effect WhatToSay() []u8;

fn helloEffect() effect{WhatToSay, Some}#void {
    if Some("Give me a bool.").perform {
        println(WhatToSay().perform);
    } else {
        println("It's false");
    }
}

handler {
    -- no catched field
    fn handleSome(data: []u8) bool {
        println(data);
        true
    }
    fn handleWhatToSay() []u8 {
        "Whatever you what to say"
    }
}



# deny effect-ask in effect handling block
pub fn main() !void {
    let str = "hello".toString();
    helloEffect()# {
        Some(data) => { 
            -- Obviously, this statement still running inside the main function
            if data().toString().len() > 64 { return error.HeyPanic; }
            -- Fn([]u8) void
            println(str.asStr()); 
            -- FnOnce(String) void
            println(str); 
            true
        },
        WhatToSay => "Whatever you what to say",
    }! { err -> 
        println(tagName!(err));
    }
}

effect Some(^Display) bool;
effect WhatToSay() []u8;

fn helloEffect() 
    effect{WhatToSay, Some}#
    error{HaHaJustAError}!void {
    for _ in 1..10 {
        if Some("Give me a bool.").perform {
         println(WhatToSay().perform);
        } else {
        println("It's false");
        }
    }
    
    error.HaHaJustAError
}
