### PHP 5.3

PHP 5.3 ist eigentlich PHP 6 **ohne** Unicode-Unterstützung.


#### Wichtige neue Sprach-Konstrukte die mit PHP 5.3 eingeführt wurden:

 * Namespaces
 * Late Static Binding
 * Closures
 * NOWDOC (Wie HEREDOC nur mit einfachen Anführungszeichen)
 * Sprungmarken
 * Konstantendeklaration mit "const"
 * Ausnahmen können verschachtelt werden


### Namespaces

Bessere Organisation und Lesbarkeit des Codes

    namespace Foo;
    
    use Bar\Foo as BarFoo;
    
    class Baz extends BarFoo {
        public function doSomething() {
            echo 'doing something';
        }
    }
    
    $baz = new \Foo\Baz();
    $baz->doSomething();
    
    // doing something;


### Late Static Binding

    class Bar {
    
        const NAME = 'Bar';
        
        public function getSelfName() {
            return self::NAME;
        }
        
        public function getStaticName() {
            return static::NAME;
        }
    }
    
    class Foo extends Bar {
        const NAME = 'Foo';
    }
    
    $x = new Foo();
    $x->getSelfName();    // Bar
    $x->getStaticName();  // Foo


### Closures

(Anonyme Funktionen wie z.B. aus JavaScript)

    $b = 'PHPUG_'
    $f = array_map(function($a) use ($b){
        return $b . strtoupper($a);
    }, array('foo', 'bar', 'baz'));
    
    print_r($f);
    
    // array('PHPUG_FOO', 'PHPUG_BAR', 'PHPUG_BAZ');


### NOWDOC

NOWDOC ist *fast* dasselbe wie HEREDOC. 
Es wird *nur* nicht geparst. 

    $count = 5;
    $f = <<<'EOT'
    echo 'foo';
    hier stehen $count Informationen
    EOT;
    
    echo $f;
    
    // echo 'foo';
    // hier stehen $count Informationen


### Konstantendeklaration mit "const"

    <?php
    const FOO = 'foo';
    
    define('FOO', 'foo');


### Verschachtelte Ausnahmen

    try {
        throw new Exception('Help', 110);
    } catch (Exception $e) {
    
        // Der dritte Parameter ist der interessante Teil!
        throw new Exception('More Help', 112, $e);
    }


### Sprungmarken (GOTO)

In meinen Augen eine Reminiszenz an Prozedurales Programmieren....

    10 PRINT "Hallo"
    20 GOTO 10

<small>Die hektischen Versuche der Mitarbeiter der Computerabteilung eines großen Warenhauses das abzustellen
 
**Unbezahlbar** 

(So wie auch der Computer....)</small>


### Sprungmarken (GOTO)

    echo 'Hallo';
    
    goto welt;
    
    echo 'schöne neue';
    
    welt:
    
    echo 'Welt';
    
    // Hallo Welt

    
    

