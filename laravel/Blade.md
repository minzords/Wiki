---
title: Introduction à Blade
description: 
published: true
date: 2023-04-17T11:08:53.923Z
tags: 
editor: markdown
dateCreated: 2023-04-17T11:07:18.166Z
---

# Le IF
```php
	@if (count($records) === 1)
    Cas 1
	@elseif (count($records) > 1)
    Cas 2
	@else
    Cas 3
@endif
```

# Le Switch
```php
	@switch($i)
    @case(1)
        First case...
        @break
 
    @case(2)
        Second case...
        @break
 
    @default
        Default case...
	@endswitch
```

# Le Foreach

```php
	@foreach ($users as $user)
    <li>{{ $user->name }}</li>
	@endforeach
```

## Options disponibles

```php
	@continue($user->type == 1)
```
	
```php
	@break($user->number == 5)
```

# Le For
```php
	@for ($i = 0; $i < 10; $i++)
    The current value is {{ $i }}
	@endfor
```

# Le while
```php
	@while (true)
    <p>I'm looping forever.</p>
	@endwhile
```