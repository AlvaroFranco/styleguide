#[[NSAluana alloc] initWithStyleGuide:@"Objective-C"];
------------------------------------------------------

*Objective-C at its finest*

##Table of contents

  1. [Types](#types)
  1. [Operators](#operators)
  1. [Objects](#objects)
  1. [Spacing and line breaking](#spacing)
  1. [Methods](#methods)
  1. [Conditionals and Loops](#conditionals-and-loops)
  1. [Blocks](#blocks)
  1. [Enums](#enums)
  1. [Delegates](#delegates)
  1. [Import](#import)
 
##Types

- **NSInteger vs int**: Always use Cocoa types instead of the C ones. NSInteger instead of int/long, CGFloat instead of float/double, so you have not to specify when in 32 or 64 bits.
	
		NSInteger foo = 1;
	
		CGFloat bar = 1;
		
**[⬆ back to top](#table-of-contents)**

#Operators

- **Operators**: Operators separated should always be surrounded by spaces unless there is only one operand.

		NSString *foo = @"foo";
	
		NSInteger bar = 5; // 5
		bar += 4; // 9
		bar++; // 10
		bar = 45 + 7; // 52
 
##Objects

- **Class initialisation**: Always use ```-new``` instead of ```alloc init```.

		FooClass *foo = [FooClass new];
		
- **Arrays, dictionarys and strings**: Keep it simple: get rid of ```-new``` when possible, for example, when creating a **non-mutable** and simple array, dictionary or string.

		NSString *fooString = @"Foo";
		
		NSArray *fooArray = @[@"foo", @"bar"];
		
		NSDictionary *fooDict = @{@"fooKey": @"fooValue", @"barKey": @"barValue"};
		
**[⬆ back to top](#table-of-contents)**

##Spacing and line breaking

- **Method**: When declaring a method, always join the - and the return value. The name of the method should explain briefly what is that method for.

		-(returnType)nameOfTheMethodWithArg1:(arg)arg1 andArg2:(arg)arg2;
		
	When executing a method, it must be always in 1 single line, without line breakings. Also, there shouldn't be a space between the : symbol and the variable.

		[self nameOfTheMethodWithArg1:arg1 andArg2:arg2];
		
	When stacking some methods, always put a space where the new method starts:
	
		[[NSFoo alloc] initWithArg:foo];
		
	When writting stuff into a method, **never** take the bracket to the next line, always right after the name of the method, separed with 1 single space. Then, put a line breaking and start writting code.
	
		-(void)nameOfTheMethodWithArg1:(arg)arg1 andArg2:(arg)arg2 {
		
			// Write stuff
		

- **Property and variable**: **Always use camelCase**. There should always be a space between the property class and the * symbol, and this symbol must be joined to the property name. On the properties, if nonatomic is included in the declaration, it always goes first. In the case of the variables, without the * symbol, there must be 1 single space between the type and the variable name. 

		@property (nonatomic, strong) NSString *foo;

		CGRect bar;
		
	Also, instance a property with a point instead of with a method structure.
	
		NSString *foo = segue.identifier; // Good
		
		NSString *foo = [segue identifier]; // Bad
		
- **NSLog**: Right after the quotes closure, put a comma and a space. Then, write all the arguments followed by a comma and a space, except the last one.

		NSLog(@"%@ and rect height %f", foo, bar.size.height);
		
- **NSArray and NSDictonary**: In case of an array, write the objects followed by commas and a space right after the comma.

		NSArray *fooArray = @[@"foo", @"bar"];

	On a dictionary, the keys are followed by the : symbol without the space, which goes right after the symbol, followed by the value.
	
		NSDictionary *fooDict = @{@"fooKey": @"fooValue", @"barKey": @"barValue"};
	
	In case the dictionary gets too big, it could be displayed vertically:
		
		NSDictionary *fooDict = @{
									@"fooKey": @"fooValue",
									@"barKey": @"barValue"
								  };
								 
- **Conditionals**: Right after the conditionals, put a line breaking, between the brackets. Also, the if structure must **always** be made with brackets. Some examples:

		if (foo == 1) {
			
			// Do something
		}
		
		for (NSArray *fooArray in fooDictionary) {
			
			// Do something
		}
		
		do {
		
			// Do something
		} while (foo == 1)

**[⬆ back to top](#table-of-contents)**

##Methods

- **Declaration**: Try to explain briefly what that method is for. Don't make it too short but don't make it too long either. If it has arguments, the variables should explain itself what they are going to do or what they have stored. Try to keep it simple but understandable. For example, let's say we need a method to return us the center point (CGPoint) of a rect (CGRect):

		-(CGPoint)cntrRct:(CGRect)arg; // Bad!
		
		-(CGPoint)centerOfRect:(CGRect)rect; // Neat!
		
		-(CGPoint)centerPointGeneratedFromRect:(CGRect)originalRect; // Bad!
		
**[⬆ back to top](#table-of-contents)**
		
##Conditionals and loops

- **for and forin structures**: When possible, use ```forin``` structure instead of ```for``` structure.

		for (NSArray *fooArray in fooDictionary) {
			
			// Good
		}
		
		for (int i = 0; i < fooDictionary.count; i ++) {
			
			NSArray *fooArray = fooDictionary[i];
			
			// Bad
		}
		
- **if structure**: Always use brackets, never use the simplified version.

		if (foo == 1) {
		
			// Good!
		}
		
		if (foo == 1)
			// Bad!
			
**[⬆ back to top](#table-of-contents)**
			
##Blocks

- **Declaration**: Blocks should be declared as a ```typedef```:

		typedef void (^blockName)(arg *arg1, arg *arg2);
		
- **Invoke**: If the blocks has no arguments, use ```-invoke```. 

		[block invoke];
		
	If not, go the normal way:
	
		block(arg1, arg2);
		
**[⬆ back to top](#table-of-contents)**

##Enums

- **Declaration**: Like the blocks, enums should be declared as ```typedef``` using ```NS_ENUM```:

		typedef NS_ENUM (NSInteger, FooType) {
		
			FooType1,
			FooType2,
			FooType3
		};

**[⬆ back to top](#table-of-contents)**

##Delegates

- **Declaration**:

		@protocol FooDelegate <NSObject>
		
		// Some delegate methods
		
		@end

		@interface Foo : NSObject
	
		@property (nonatomic, retain) id<FooDelegate> fooDelegate;
		
		@end
		
**[⬆ back to top](#table-of-contents)**

##Import 

- ** #import vs @class**: When possible, use `@class` instead of `#import` since it provides a slightly compiler time performance boost.

According to Apple:

> The @class directive minimizes the amount of code seen by the compiler and linker, and is therefore the simplest way to give a forward declaration of a class name. Being simple, it avoids potential problems that may come with importing files that import still other files. For example, if one class declares a statically typed instance variable of another class, and their two interface files import each other, neither class may compile correctly.

- **Header Prefix**: If you're using a certain class or framework in your target/project, use `Header prefix`,

		#ifdef __OBJC__	
    		#import <Foundation/Foundation.h>
    		#import <UIKit/UIKit.h>
    		#import <CoreText/CoreText.h>
		#endif
		
