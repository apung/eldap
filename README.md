## Laravel and LDAP ##

[![Build Status](https://travis-ci.org/apung/eldap.svg)](https://travis-ci.org/apung/eldap)
[![Total Downloads](https://poser.pugx.org/apung/ldap/downloads.svg)](https://packagist.org/packages/apung/ldap)
[![Latest Stable Version](https://poser.pugx.org/apung/ldap/v/stable.svg)](https://packagist.org/packages/apung/ldap)
[![Latest Unstable Version](https://poser.pugx.org/apung/ldap/v/unstable.svg)](https://packagist.org/packages/apung/ldap)
[![License](https://poser.pugx.org/apung/ldap/license.svg)](https://packagist.org/packages/apung/ldap)

### Installing ###
```
composer require apung\ldap
```

### Integrating ###
```
'providers' => array(
    ....
    'Apung\Ldap\LdapServiceProvider',
    ....
),
```

### Usage ###

```
$options = array(
            'host'=>'ldap.example.com',
            'port'=>389,
            'base_dn'=>'dc=example,dc=com',
            'bind_rdn'=>'cn=admin,dc=example,dc=com',
            'bind_pw'=>'ManagerPassword!!!'
        );

$ldap = new \Apung\Ldap\Ldap($options);

//search person (which have uid) inside ou=people,dc=exampe,dc=com
$select = $ldap->select('uid')->from('ou=people,dc=example,dc=com')->where(array('uid'=>'*'))->get();

//like above, but return DN
$select = $ldap->select('uid')->from('ou=people,dc=example,dc=com')->where(array('uid'=>'*'))->withdn()->get();

//like above, but return all attributes (inside select statement)
$select = $ldap->select(array('uid','givenname'))->from('ou=people,dc=example,dc=com')->where(array('uid'=>'*'))->getAll();
```

### TODO ###
TODO:
* CRUD (Create / Read / Update / Delete) statements
* Documentation