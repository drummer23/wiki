# Doctrine

## Which is the owning side of an association?

Imagine the situation below.

In the Member entity, you have the inversedBy attribute of the association annotation. This attribute shows, which field contains the inversing property at the inversed side.

```php
/**
 * @ManyToOne(targetEntity="Club", inversedBy="members")
 */
protected $club;
```
http://docs.doctrine-project.org/projects/doctrine-orm/en/latest/reference/annotations-reference.html#manytoone

In the Club entity, there exists the attribute mappedBy. This defines, which property points to this entity. As the documentation mentions, this attribue is required at the inversed side.

```php
/**
 * @OneToMany(targetEntity="Member", mappedBy="club")
 */
public $members;
```
http://docs.doctrine-project.org/projects/doctrine-orm/en/latest/reference/annotations-reference.html#annref-onetomany

### Owning side of an association

The owning side contains the inversedBy-attribute.
The inversed side contains the mappedBy-attribute.

Read more about owning sides and why it's important to have one:
http://docs.doctrine-project.org/projects/doctrine-orm/en/latest/reference/unitofwork-associations.html#association-updates-owning-side-and-inverse-side
