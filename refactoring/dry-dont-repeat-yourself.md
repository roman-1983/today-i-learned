# DRY - Don’t Repeat Yourself

**DRY helps you to fix the "Duplicate Code" code smell.**

I came into a running symfony project weeks ago. After digging to the already produced code i found some parts, that should really be optimized.
So we decided as a team to refactor some code-parts to make the software more readable, better expandable and make it easier to maintain it.

I learned that there are severals methods to refactor a part of code. Today i learned about the DRY rule which means:
> Do not repeat yourself!

Developers detect parts that really require a refactoring by its "Code Smell". 
The more experience a developer has, the better he smells code smell.

But you really do not need your nose to detect "Code Smell" - you need your eyes. ;-)

In the following code example i learned how to fix "Duplicate code" code smell via DRY.

Example with "Duplicate Code" code smell.

    <?php
    class PartnerOneConnection {
        private $settings;
    
        public function __construct( $settings ) {
            $this->set_settings( $settings );
        }
    
        protected function set_settings( $settings ) {
            if ( ! is_array( $settings ) ) {
                throw new \Exception( 'Invalid settings' );
            }
            $this->settings = $settings;
        }
        
        protected function connect() {
            //...
        }
    }
    
    class PartnerTwoConnection {
        private $settings;
        
        public function __construct( $settings ) {
            $this->set_settings( $settings );
        }
    
        protected function set_settings( $settings ) {
            if ( ! is_array( $settings ) ) {
                throw new \Exception( 'Invalid settings' );
            }
            $this->settings = $settings;
        }
        
        protected function connect() {
            //...
        }
    }
    
To refactor the example and respect DRY, i have done this:
- Introduced a new `AbstractConnection`
- Moved `setSettings` into the `AbstractConnection`
- Moved `connect` into the `AbstractConnection`
- Made `PartnerOneConnection` and `PartnerTwoConnection` to extend `AbstractConnection`
    
Example which respects the DRY rule "Do not repeat yourself".

    <?php 
     abstract class AbstractConnection {
         protected $settings;

         public function __construct( $settings ) {
             $this->set_settings( $settings );
         }

         protected function set_settings( $settings ) {
             if ( ! is_array( $settings ) ) {
                 throw new \Exception( 'Invalid settings' );
             }
             $this->settings = $settings;
         }
         
         public abstract function connect();
     }
     
     class PartnerOneConnection extends AbstractConnection {
         protected function connect() {
             //...
         }
     }
     
     class PartnerTwoConnection extends AbstractConnection {
         protected function connect() {
             //...
         }
     }