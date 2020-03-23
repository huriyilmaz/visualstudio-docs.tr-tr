---
title: Python kodunu biçimlendir
description: Visual Studio, boşluk, deyimler, sarma ve açıklamalar dahil olmak üzere Python kodunu otomatik olarak yeniden biçimleyebilir.
ms.date: 03/13/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 6e95d05c3fbc0dd46d235c7480bd4a9caa48947e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62957547"
---
# <a name="format-python-code"></a>Python kodunu biçimlendir

Visual Studio, önceden yapılandırılmış biçimlendirme seçeneklerini eşleştirmek için kodu hızla yeniden biçimlendirmenizi sağlar.

- Seçimi biçimlendirmek için:**Gelişmiş** > **Biçim Seçimini** **Edit'i** > seçin veya **Ctrl**+**E** > **F**tuşuna basın.
- Dosyanın tamamını biçimlendirmek için: > **Gelişmiş** > Biçim**Belgesini** **Edit'i**seçin veya **Ctrl**+**E** > **D**tuşuna basın.

Seçenekler **Araçlar** > **Seçenekleri** > Metin**Düzenleyicisi** > **Text Editor** > Python**Biçimlendirme** ve iç içe sekmeleri aracılığıyla ayarlanır. Bu seçeneklerin görünmesi için **tüm ayarları göster'i** seçmeniz gerekir:

![Visual Studio'da Python biçimlendirme seçenekleri](media/options-editor-formatting.png)

Varsayılan olarak biçimlendirme seçenekleri [PEP 8 stil kılavuzunun](https://www.python.org/dev/peps/pep-0008/)bir üst kümesiyle eşleşecek şekilde ayarlanır. **Genel** sekmesi biçimlendirmenin ne zaman uygulanacağı belirlenir; diğer üç sekme için ayarlar bu makalede açıklanmıştır.

[Visual Studio'daki Python desteği,](installing-python-support-in-visual-studio.md) daha sonraki bir bölümde açıklandığı gibi **Gelişmiş'i Edit** > **Advanced** menüsüne yararlı [**Dolgu Yorum Paragrafı**](#fill-comment-paragraph-command) komutunu da ekler.

## <a name="spacing"></a>Aralık

Çeşitli dil yapılarının etrafına boşlukların eklendiği veya kaldırıldığı **boşluk** denetimleri. Her seçeneğin üç olası değeri vardır:

- Kontrol: aralığın uygulanmasını sağlar.
- Temizlendi: herhangi bir boşluk kaldırır.
- Belirsiz: özgün biçimlendirmeyi yerinde bırakır.

Çeşitli seçeneklere örnekler aşağıdaki tablolarda verilmiştir:

| Sınıf tanımları seçeneği | İşaretli | Temizlenmiş |
| --- | --- | --- |
| **Sınıf bildiriminin adı ve üslistesi arasına boşluk ekleme** | `class X (object): pass` | `class X(object): pass` |
| **Üsler listesi parantez içinde boşluk ekleme** | `class X( object ): pass` | `class X(object): pass` |
| **Boş bazlar listesi paranteziçinde boşluk ekleme** | `class X( ): pass` | `class X(): pass` |

<br/>

| İşlev tanımları seçeneği | İşaretli | Temizlenmiş |
| --- | --- | --- |
| **İşlev bildiriminin adı ve parametre listesi arasına boşluk ekleme** | `def X (): pass` | `def X(): pass` |
| **Parametre listesi paranteziçinde boşluk ekleme** | `def X( a, b ): pass` | `def X(a, b): pass` |
| **Boş parametre listesi paranteziçinde boşluk ekleme** | `def X( ): pass` | `def X(): pass` |
| **Varsayılan parametre değerlerinde '=' etrafında boşluk ekleme** | `includes X(a = 42): pass` | `includes X(a=42): pass` |
| **İade ek açıklama işleçleri önce ve sonra boşluk ekleme** | `includes X() -> 42: pass` | `includes X()->42: pass` |

<br/>

| Operatörler seçeneği | İşaretli | Temizlenmiş |
| --- | --- | --- |
| **İkili işleçler etrafında boşluk ekleme** | `a + b` | `a+b` |
| **Atamaların etrafına boşluk ekleme** | `a = b` | `a=b` |

<br/>

| İfade aralığı seçeneği | İşaretli | Temizlenmiş |
| --- | --- | --- |
| **İşlev çağrısının adı ve bağımsız değişken listesi arasına boşluk ekleme** | `X ()` | `X()` |
| **Boş bağımsız değişken listesi paranteziçinde boşluk ekleme** | `X( )` | `X()` |
| **Bağımsız değişken listesi paranteziçinde boşluk ekleme** | `X( a, b )` | `X(a, b)` |
| **İfade parantezi içinde boşluk ekleme** | `( a )` | `(a)` |
| **Boş tuple parantez içinde boşluk ekleme** | `( )` | `()` |
| **Tuple parantez içinde boşluk ekleme** | `( a, b )` | `(a, b)` |
| **Boş kare köşeli ayraçlar içinde boşluk ekleme** | `[ ]` | `[]` |
| **Listelerin kare ayraçlarına boşluk ekleme** | `[ a, b ]` | `[a, b]` |
| **Kare ayraç açmadan önce boşluk ekleme** | `x [i]` | `x[i]` |
| **Kare ayraçlar içinde boşluk ekleme** | `x[ i ]` | `x[i]` |

<br/>

## <a name="statements"></a>Deyimler

**Deyimler** seçenekleri, çeşitli deyimlerin daha Pythonik formlara otomatik olarak yeniden yazılmasının denetimine.

| Seçenek | Biçimlendirmeden önce | Biçimlendirmeden sonra |
| --- | --- | --- |
| **İthal modülleri yeni hatta yerleştirin** | `import sys, pickle` | `import sys`<br/>`import pickle` |
| **Gereksiz yarım kolonları kaldırın** | `x = 42;` | `x = 42` |
| **Yeni satırlara birden çok deyim yerleştirme** | `x = 42; y = 100` | `x = 42`<br/>`y = 100` |

## <a name="wrapping"></a>Kaydırma

**Sarma,** Maksimum **yorum genişliğini** ayarlamanızı sağlar (varsayılan değer 80'dir). Çok **geniş** bir seçenek olan Kaydırma yorumları ayarlanırsa, Visual Studio yorumları bu maksimum genişliği aşmamak için yeniden biçimlenir.

```python
# Wrapped to 40 columns
# There should be one-- and preferably
# only one --obvious way to do it.
```

```python
# Not-wrapped:
# There should be one-- and preferably only one --obvious way to do it.
```

## <a name="fill-comment-paragraph-command"></a>Açıklama Paragrafı komutunu doldur

**Edit**+**E** > **P****Advanced****Ctrl****Fill Comment Paragraph** Gelişmiş Dolgu Yorum Paragrafı (Ctrl E P) yeniden akışlarını ve yorum metnini biçimlendirin, kısa satırları birleştirin ve uzun satırları ayırın. >  > 

Örnek:

```python
# foo
# bar
# baz
```

değişiklikler:

```python
# foo bar baz
```

```python
# This is a very long long long long long long long long long long long long long long long long long long long comment
```

değişiklikler:

```python
# This is a very long long long long long long long long long long long long
# long long long long long long long comment
```
