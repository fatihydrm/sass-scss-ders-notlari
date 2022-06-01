# scss kunlanım notları

| Sayı |             Konu              |
| ---- | :---------------------------: |
|  001 | [Degisken](#değişken)       |
|  002 | [İç içe yazma](#iç-içe-yazma)       |
|  003 | [Modüler](#modüler)       |
|  004 | [Mixins (karışımlar)](#mixins-karışımlar)       |
|  ____ |______________________________________ |

## Değişken
> değişken tanımlama

```scss
$text-color: #FFFFFF;
$bg-color: #222222;

div{
  color:$text-color;
  background:$bg-color;
}

```

## iç içe yazma
> sass ile iç içe eleman yapısını kunlanabilirsiniz.

```scss
div{
  color:#222;
  background:#eee;
  
  &:hover{
    background:#333;
  }
  &:active{
    background:#212121;
  }
  
  & > .item{
    color:#fff;
    
    & > img{
      width:200px;
      height:200px;
    }
  }
  
}

```

## Modüler
> sass  modül yapısı sayesinde başka sass dosyalarını ana sass dosyasına @use ile dahil edebilirsiniz bu sayede böl yarçala yaparak rahat kod yazabilirsiniz.

```scss
// _farklidosya.scss
$text-color: #FFFFFF;
$bg-color: #222222;

div{
  color:$text-color;
  background:$bg-color;
}
```


```scss
// ana.scss
@use 'farklidosya';

.div {
  background-color: farklidosya.$bg-color;
  color: #fff;
}
```

## Mixins (karışımlar)
> sass içerisindeki Mixins yapısı sayesinde kod tekrarından kurtulun! js içerisindeki fonksiyonlara benzetebilirsiniz.

```scss
@mixin tema($degisken: #222) {
  background: $degisken;
  box-shadow: 0 0 1px rgba($degisken, .25);
  color: #fff;
}

.bilgi {
  @include tema;
}
.uyarı {
  @include tema($degisken: red);
}
.basarili {
  @include tema($degisken: green);
}
```
