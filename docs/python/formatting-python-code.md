---
title: Python kodunu biçimlendirme
description: Visual Studio, deyimler, sarmalama ve açıklamalar dahil olmak üzere Python kodunu otomatik olarak yeniden biçimlendirebilirsiniz.
ms.date: 03/13/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: b6852d06048acf86f50c8d56fb91bc8a298ec949d77d9a23afef5cc56adb68ae
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121230202"
---
# <a name="format-python-code"></a>Python kodunu biçimlendirme

Visual Studio önceden yapılandırılmış biçimlendirme seçenekleriyle eşleşmesi için kodu hızla yeniden biçimlendirmenizi sağlar.

- Seçimi biçimlendirmek için: Gelişmiş Biçim **Seçimini**  >  **Düzenle'yi**  >  **seçin veya** Ctrl E F  +   >  **tuşlarına basın.**
- Dosyanın tamamını biçimlendirmek için: Gelişmiş Biçim **Belgesini**  >  **Düzenle'yi**  >  **seçin veya** Ctrl E D  +   >  **tuşlarına basın.**

Seçenekler, Araçlar Seçenekler **Metin**  >  **Düzenleyici**  >  Python **Biçimlendirmesi**  >    >  **ve iç** içe geçmiş sekmeleri aracılığıyla ayarlanır. Bu seçeneklerin görünmesi **için Tüm ayarları** göster'i seçmeniz gerekir:

![Visual Studio'da Python biçimlendirme seçenekleri](media/options-editor-formatting.png)

Biçimlendirme seçenekleri varsayılan olarak PEP 8 stil kılavuzunun bir üst [kümesiyle eşşecek şekilde ayarlanır.](https://www.python.org/dev/peps/pep-0008/) Genel **sekmesi** biçimlendirmenin ne zaman uygulandığını belirler; diğer üç sekmenin ayarları bu makalede açıklanmıştır.

[Visual Studio'da Python](installing-python-support-in-visual-studio.md) desteği, sonraki [](#fill-comment-paragraph-command) bir bölümde açıklandığı gibi gelişmiş menüyü düzenle menüsüne yararlı  >   AçıklamaYı Doldur komutunu da ekler.

## <a name="spacing"></a>Aralık

**Boşlukların** çeşitli dil yapılarının etrafında yerleştirildiğinde veya kaldırıldığı aralık denetimleri. Her seçeneğin üç olası değeri vardır:

- İşaretli: Aralığın uygulandığını doğrular.
- Temiz: Boşlukları kaldırır.
- Belirsiz: Özgün biçimlendirmeyi yerinde bırakır.

Çeşitli seçeneklere örnekler aşağıdaki tablolarda verilmiştir:

| Sınıf tanımları seçeneği | İşaretli | Temizlenmiş |
| --- | --- | --- |
| **Sınıf bildiriminin adı ve temel listesi arasına boşluk ekleme** | `class X (object): pass` | `class X(object): pass` |
| **Tabanlar listesi parantezleri içine boşluk ekleme** | `class X( object ): pass` | `class X(object): pass` |
| **Boş tabanlar listesi parantezleri içine boşluk ekleme** | `class X( ): pass` | `class X(): pass` |

<br/>

| İşlev tanımları seçeneği | İşaretli | Temizlenmiş |
| --- | --- | --- |
| **İşlev bildiriminin adı ve parametre listesi arasına boşluk ekleme** | `def X (): pass` | `def X(): pass` |
| **Parametre listesi parantezleri içine boşluk ekleme** | `def X( a, b ): pass` | `def X(a, b): pass` |
| **Boş parametre listesi parantezleri içine boşluk ekleme** | `def X( ): pass` | `def X(): pass` |
| **Varsayılan parametre değerlerine '=' çevresinde boşluk ekleme** | `includes X(a = 42): pass` | `includes X(a=42): pass` |
| **Dönüş ek açıklaması işleçleri öncesinde ve sonrasında boşluk ekleme** | `includes X() -> 42: pass` | `includes X()->42: pass` |

<br/>

| İşleçler seçeneği | İşaretli | Temizlenmiş |
| --- | --- | --- |
| **İkili işleçlerin etrafına boşluk ekleme** | `a + b` | `a+b` |
| **Atamaların etrafına boşluk ekleme** | `a = b` | `a=b` |

<br/>

| İfade aralığı seçeneği | İşaretli | Temizlenmiş |
| --- | --- | --- |
| **İşlev çağrısının adı ve bağımsız değişken listesi arasına boşluk ekleme** | `X ()` | `X()` |
| **Boş bağımsız değişken listesi parantezleri içine boşluk ekleme** | `X( )` | `X()` |
| **Bağımsız değişken listesi parantezleri içine boşluk ekleme** | `X( a, b )` | `X(a, b)` |
| **İfadenin parantez içine boşluk ekleme** | `( a )` | `(a)` |
| **Boş çift ayraç içine boşluk ekleme** | `( )` | `()` |
| **Ayraç içine boşluk ekleme** | `( a, b )` | `(a, b)` |
| **Boş köşeli ayraç içine boşluk ekleme** | `[ ]` | `[]` |
| **Listelerin köşeli ayraç içine boşluk ekleme** | `[ a, b ]` | `[a, b]` |
| **Köşeli ayraç açılmadan önce boşluk ekleme** | `x [i]` | `x[i]` |
| **Köşeli ayraç içine boşluk ekleme** | `x[ i ]` | `x[i]` |

<br/>

## <a name="statements"></a>Deyimler

Deyimler **seçenekleri,** çeşitli deyimlerin otomatik olarak daha Python biçimlerinde yeniden yazılabilir hale otomatik olarak yazılabilir.

| Seçenek | Biçimlendirmeden önce | Biçimlendirmeden sonra |
| --- | --- | --- |
| **İçe aktarılan modülleri yeni satıra yer** | `import sys, pickle` | `import sys`<br/>`import pickle` |
| **Gereksiz noktalı virgülleri kaldırma** | `x = 42;` | `x = 42` |
| **Yeni satırlara birden çok deyimleri yer** | `x = 42; y = 100` | `x = 42`<br/>`y = 100` |

## <a name="wrapping"></a>Kaydırma

**Sarmalama,** En fazla açıklama **genişliğini (varsayılan** değer 80) ayarlamaya olanak sağlar. Çok **geniş olan açıklamalarını sarmala** seçeneği ayarlanırsa, Visual Studio genişliği aşmamalarını istediğiniz şekilde yeniden biçimlendirin.

```python
# Wrapped to 40 columns
# There should be one-- and preferably
# only one --obvious way to do it.
```

```python
# Not-wrapped:
# There should be one-- and preferably only one --obvious way to do it.
```

## <a name="fill-comment-paragraph-command"></a>Açıklama Paragrafı Doldur komutu

**Düzenle**  >  **Gelişmiş**  >  **Açıklama Paragrafı Doldur** (**Ctrl** E P ) açıklama metnini yeniden akışları ve biçimlerini kullanarak kısa satırları bir araya getirdi +   >  ve uzun olanları parçaladı.

Örnek:

```python
# foo
# bar
# baz
```

şu değişikliklere göre değişir:

```python
# foo bar baz
```

```python
# This is a very long long long long long long long long long long long long long long long long long long long comment
```

şu değişikliklere göre değişir:

```python
# This is a very long long long long long long long long long long long long
# long long long long long long long comment
```
