---
title: Python kodunu biçimlendirme
description: Visual Studio, boşluk, deyimler, kaydırma ve açıklamalar dahil Python kodunu otomatik olarak yeniden biçimlendirebilir.
ms.date: 03/13/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 7b03e99a70edd587c9dfe2a43d326a64d14b9193
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887893"
---
# <a name="format-python-code"></a>Python kodunu biçimlendirme

Visual Studio, önceden yapılandırılmış biçimlendirme seçenekleriyle eşleşecek şekilde kodu hızlı bir şekilde yeniden biçimlendirmenizi sağlar.

- Bir seçimi biçimlendirmek için:   >  **Gelişmiş**  >  **Biçim seçimini** Düzenle ' yi seçin veya **CTRL** + **E**  >  **F** tuşlarına basın.
- Tüm dosyayı biçimlendirmek için:   >  **Gelişmiş**  >  **Biçim belgesini** Düzenle ' yi seçin veya **CTRL** + **E**' ye basın  >  .

Seçenekler, **Araçlar**  >  **Seçenekler**  >  **metin Düzenleyicisi**  >  **Python**  >  **biçimlendirme** ve iç içe geçmiş sekmeleri aracılığıyla ayarlanır. Bu seçeneklerin görünmesi için **tüm ayarları göster** ' i seçmeniz gerekir:

![Visual Studio 'da Python biçimlendirme seçenekleri](media/options-editor-formatting.png)

Biçimlendirme seçenekleri varsayılan olarak [Pep 8 stil kılavuzunun](https://www.python.org/dev/peps/pep-0008/)bir üst kümesiyle eşleşecek şekilde ayarlanır. Biçimlendirmenin ne zaman uygulanacağını **genel** sekme belirler. diğer üç sekmeye yönelik ayarlar bu makalede açıklanmıştır.

[Visual Studio 'da Python desteği](installing-python-support-in-visual-studio.md) Ayrıca, daha sonraki bir bölümde açıklandığı gibi, gelişmiş bir [**Açıklama Ekle paragraf**](#fill-comment-paragraph-command) komutunu da   >  **Gelişmiş** Düzenle menüsüne ekler.

## <a name="spacing"></a>Aralık

**Boşluk denetimleri,** boşlukların çeşitli dil yapıları içine eklendiği veya kaldırıldığı yerdir. Her seçenekte üç olası değer vardır:

- İşaretlendi: aralığın uygulanmış olmasını sağlar.
- Temizlenmiş: herhangi bir boşluğu kaldırır.
- Belirsiz: özgün biçimlendirmeyi yerinde bırakır.

Çeşitli seçeneklere yönelik örnekler aşağıdaki tablolarda verilmiştir:

| Sınıf tanımları seçeneği | İşaretli | Temizlenen |
| --- | --- | --- |
| **Sınıf bildiriminin adı ve tabanı listesi arasına boşluk Ekle** | `class X (object): pass` | `class X(object): pass` |
| **Taban tabanı liste ayraçları içine boşluk Ekle** | `class X( object ): pass` | `class X(object): pass` |
| **Boş taban liste ayraçları içine boşluk Ekle** | `class X( ): pass` | `class X(): pass` |

<br/>

| İşlev tanımları seçeneği | İşaretli | Temizlenen |
| --- | --- | --- |
| **İşlev bildiriminin adı ve parametre listesi arasına boşluk Ekle** | `def X (): pass` | `def X(): pass` |
| **Parametre listesi ayraçları içine boşluk Ekle** | `def X( a, b ): pass` | `def X(a, b): pass` |
| **Boş parametre listesi ayraçları içine boşluk Ekle** | `def X( ): pass` | `def X(): pass` |
| **Varsayılan parametre değerlerinde ' = ' etrafına boşluk Ekle** | `includes X(a = 42): pass` | `includes X(a=42): pass` |
| **Ek açıklama işleçlerini döndürmeden önce ve sonra boşluk Ekle** | `includes X() -> 42: pass` | `includes X()->42: pass` |

<br/>

| Operators seçeneği | İşaretli | Temizlenen |
| --- | --- | --- |
| **İkili işleçlerin çevresine boşluk Ekle** | `a + b` | `a+b` |
| **Atamaların çevresine boşluk Ekle** | `a = b` | `a=b` |

<br/>

| İfade boşluğu seçeneği | İşaretli | Temizlenen |
| --- | --- | --- |
| **İşlev çağrısının adı ve bağımsız değişken listesi arasına boşluk Ekle** | `X ()` | `X()` |
| **Boş bağımsız değişken listesi parantezlerinin içine boşluk Ekle** | `X( )` | `X()` |
| **Bağımsız değişken listesi parantezlerinin içine boşluk Ekle** | `X( a, b )` | `X(a, b)` |
| **İfadenin ayraçları içine boşluk Ekle** | `( a )` | `(a)` |
| **Boş demet ayraçları içine boşluk Ekle** | `( )` | `()` |
| **Tanımlama grubu ayraçları içine boşluk Ekle** | `( a, b )` | `(a, b)` |
| **Boş köşeli ayraçlar içine boşluk Ekle** | `[ ]` | `[]` |
| **Listelerin köşeli ayraçları içine boşluk Ekle** | `[ a, b ]` | `[a, b]` |
| **Açma köşeli ayracından önce boşluk Ekle** | `x [i]` | `x[i]` |
| **Köşeli ayraçlar içine boşluk Ekle** | `x[ i ]` | `x[i]` |

<br/>

## <a name="statements"></a>Deyimler

**Deyim** seçenekleri çeşitli deyimlerden daha pythonic formlara otomatik yeniden yazmayı denetler.

| Seçenek | Biçimlendirmeden önce | Biçimlendirmeden sonra |
| --- | --- | --- |
| **İçeri aktarılan modülleri yeni satıra yerleştir** | `import sys, pickle` | `import sys`<br/>`import pickle` |
| **Gereksiz noktalı virgül kaldır** | `x = 42;` | `x = 42` |
| **Yeni satırlara birden çok deyim yerleştirme** | `x = 42; y = 100` | `x = 42`<br/>`y = 100` |

## <a name="wrapping"></a>Sarmalama

**Kaydırma** , **en fazla açıklama genişliğini** ayarlamanıza olanak sağlar (varsayılan değer 80 ' dir). **Çok geniş bir seçenek olan sarmalama açıklamaları** ayarlanırsa, Visual Studio Yorumları bu maksimum genişliği aşmayacak şekilde yeniden biçimlendirir.

```python
# Wrapped to 40 columns
# There should be one-- and preferably
# only one --obvious way to do it.
```

```python
# Not-wrapped:
# There should be one-- and preferably only one --obvious way to do it.
```

## <a name="fill-comment-paragraph-command"></a>Açıklama paragrafını Doldur komutu

**Düzenle**  >  **Gelişmiş**  >  **Açıklama paragrafını doldur** (**CTRL** + **E**  >  **P**) Açıklama metnini yeniden akıtır ve biçimlendirir, kısa çizgileri birleştirerek ve uzun olanları parçalayabilirsiniz.

Örneğin:

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
