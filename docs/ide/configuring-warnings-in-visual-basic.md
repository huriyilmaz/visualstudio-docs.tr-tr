---
title: Visual Basic'teki Uyarıları Yapılandırma
description: Daha az hatayla daha temiz, Visual Basic daha iyi kod yazmanıza yardımcı olacak uyarılar yapılandırmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- errors [Visual Basic], warnings
- run-time errors, warnings
- warnings, configuring
ms.assetid: 99cf4781-bd4d-47b4-91b9-217933509f82
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 034f995b5dfdfbba69aafd8b5bbe5bc047fdcba3c0f83e232bba8df53b05d03d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121413264"
---
# <a name="configuring-warnings-in-visual-basic"></a>Visual Basic'da uyarıları yapılandırma

Derleyici, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] çalışma zamanı hatalarına neden olan kod hakkında bir dizi uyarı içerir. Daha az hatayla daha temiz, daha hızlı ve daha iyi kod yazmak için bu bilgileri kullanabilirsiniz. Örneğin, kullanıcı atanmamış bir nesne değişkeninin bir üyesini çağırmaya, dönüş değerini ayarlamadan bir işlevden geri dönmeye veya özel durumları yakalamak için mantıkta hatalarla bir blok yürütmeye çalışırsa derleyici bir uyarı `Try` üretir.

Bazen derleyici, kullanıcı adına ek mantık sağladığından, kullanıcının olası hataları değil, el ile ilgili göreve odaklanması gerekir. Önceki [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] sürümlerinde, **Derleyicinin** sağladığı ek mantığı sınırlamak için Option Strict [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] kullanılmıştır. Uyarıları yapılandırmak, bu mantığı tek tek uyarılar düzeyinde daha ayrıntılı bir şekilde sınırlamaya olanak sağlar.

Diğer uyarıları hatalara dönüştürerek projenizi özelleştirmek ve uygulamanıza ilgili bazı uyarıları kapatmak istiyor olabilirsiniz. Bu sayfada uyarıların tek tek nasıl aç ve kapat olduğu açıklanmaz.

## <a name="turning-warnings-off-and-on"></a>Uyarıları kapatma ve açma
Uyarıları yapılandırmanın iki farklı yolu vardır: **Project Designer'ı** kullanarak yapılandırabilirsiniz veya **/warnaserror** ve **/nowarn** derleyici seçeneklerini kullanabilirsiniz.

Project  **Tasarımcısı sayfasının Derle sekmesi** uyarıları açma ve kapatmaya olanak sağlar. Tüm uyarıları **devre dışı bırakmak için** Tüm Uyarıları Devre Dışı Bırak onay kutusunu seçin; Tüm uyarıları **hata olarak kullanmak için Tüm** Uyarıları Hata Olarak Davran'ı seçin. Bazı uyarılar görüntülenen tabloda istenen şekilde hata veya uyarı olarak görüntülenebilir.

Kesin **Seçenek Kapalı** olarak **ayarlanırsa,** Seçenek Katı **ile** ilgili uyarılar birbirinden bağımsız olarak iş olamaz. Kesin **Seçenek** Açık olarak **ayarlanırsa,** durumlarına bak fark etmez, ilişkili uyarılar hata olarak kabul edilir. Komut **satırı derleyicisinde** **belirterek Option** Strict Özel olarak ayarlanırsa, Option Strict uyarıları birbirinden bağımsız olarak açıp `/optionstrict:custom`  kapatılabilir.

Derleyicinin **/warnaserror** komut satırı seçeneği, uyarıların hata olarak kabul edip olmadığını belirtmek için de kullanılabilir. + veya - kullanarak hangi uyarıların hata veya uyarı olarak kabul edilmelidir? belirtmek için bu seçenze virgülle ayrılmış bir liste ekleyebilirsiniz. Aşağıdaki tabloda olası seçenekler ayrıntılı olarak listelemektedir.

|Komut satırı araçları|Belirler|
| - |---------------|
|`/warnaserror+`|Tüm uyarıları hata olarak davran|
|`/warnsaserror`-|Uyarıları hata olarak kabul edin. Bu varsayılan seçenektir.|
|`/warnaserror+:<warning list` `>`|Belirli uyarıları hata olarak kabul edin ve hata kimliği numarasına göre virgülle ayrılmış bir r listesi ekleyin.|
|`/warnaserror-:<warning list>`|Belirli uyarıları hata olarak kabul edin ve hata kimliği numarasına göre virgülle ayrılmış bir liste ekleyin.|
|`/nowarn`|Uyarı bildirme.|
|`/nowarn:<warning list>`|Belirtilen uyarıları, hata kimliği numaralarıyla virgülle ayrılmış bir listede listelenmiş olarak bildirme.|

Uyarı listesi, hata olarak kabul edilen uyarıların hata kimliği numaralarını içerir. Bu numaralar, belirli uyarıları açmak veya kapatmak için komut satırı seçenekleriyle birlikte kullanılabilir. Uyarı listesi geçersiz bir sayı içeriyorsa bir hata rapor edilir.

## <a name="examples"></a>Örnekler
Bu komut satırı bağımsız değişken örnekleri tablosu, her bağımsız değişkenin ne yaptığını açıklar.

|Bağımsız Değişken|Açıklama|
|--------------|-----------------|
|`vbc /warnaserror`|Tüm uyarıların hata sayılması gerektiğini belirtir.|
|`vbc /warnaserror:42024`|Uyarı 42024'ü hata olarak kabul edilmelidir.|
|`vbc /warnaserror:42024,42025`|42024 ve 42025 uyarılarının hata olarak kabul edilmelidir.|
|`vbc /nowarn`|Uyarı bildirilene bir şey olmadığını belirtir.|
|`vbc /nowarn:42024`|42024 uyarısının bildirilenem olmadığını belirtir.|
|`vbc /nowarn:42024,42025`|42024 ve 42025 uyarılarının raporlanmaz olduğunu belirtir.|

## <a name="types-of-warnings"></a>Uyarı türleri
Aşağıda, hata olarak davranmayı istemeyebilirsiniz uyarıların listesi ve ardından yer alan liste yer alıyor.

### <a name="implicit-conversion-warning"></a>Örtülü dönüştürme uyarısı
Örtülü dönüştürme örnekleri için oluşturulur. İşleci kullanırken iç sayısal türdeki örtülü dönüştürmeleri dizeye dahil `&` değildir. Yeni projeler için varsayılan ayar kapalıdır.

Kimlik: 42016

### <a name="late-bound-method-invocation-and-overload-resolution-warning"></a>Geç bağlı yöntem çağırma ve aşırı yükleme çözümleme uyarısı
Geç bağlama örnekleri için oluşturulur. Yeni projeler için varsayılan ayar kapalıdır.

Kimlik: 42017

### <a name="operands-of-type-object-warnings"></a>'Nesne' uyarısı türünde işlenenler
Türün işlenenleri oluştuğunda, Option Strict On ile `Object` **bir hata oluşturulur.** Yeni projeler için varsayılan değer açıktır.

Kimlik: 42018 ve 42019

### <a name="declarations-require-as-clause-warnings"></a>Bildirimlerde 'As' yan tümcesi uyarıları gerekli
Yan tümcesi olmayan bir değişken, işlev veya özellik bildirimi Option Strict On ile hata `As` **oluşturduğunda oluşturulur.** Atanmış bir türüne sahip değil değişkenlerin türü olduğu `Object` varsayılır. Yeni projeler için varsayılan değer açıktır.

Kimlik: 42020 (değişken bildirimi), 42021 (işlev bildirimi) ve 42022 (özellik bildirimi).

### <a name="possible-null-reference-exception-warnings"></a>Olası null başvuru özel durum uyarıları
Bir değişken, bir değer atanmadan önce kullanılmadan önce oluşturulur. Yeni projeler için varsayılan değer açıktır.

Kimlik: 42104, 42030

### <a name="unused-local-variable-warning"></a>Kullanılmayan yerel değişken uyarısı
Yerel bir değişken bildirildi ancak hiçbir zaman başvurulmayarak oluşturulur. Varsayılan değer açıktır.

Kimlik: 42024

### <a name="access-of-shared-member-through-instance-variable-warning"></a>Örnek değişkeni uyarısı aracılığıyla paylaşılan üye erişimi
Paylaşılan üyeye bir örnek üzerinden erişilirken oluşturulan veya bir örnek değişkeni aracılığıyla paylaşılan üyeye erişilirken ifadenin sağ tarafı değildir veya parametre olarak geçirilirken yan etkileri olabilir. Yeni projeler için varsayılan değer açıktır.

Kimlik: 42025

### <a name="recursive-operator-or-property-access-warnings"></a>Recursive işleci veya özellik erişim uyarıları
Bir yordamın gövdesi tanımlandığı işleci veya özelliği kullandığında oluşturulur. Yeni projeler için varsayılan değer açıktır.

Kimlik: 42004 (işleç), 42026 (özellik)

### <a name="function-or-operator-without-return-value-warning"></a>Dönüş değeri uyarısı olmayan işlev veya işleç
İşlev veya işleç belirtilen bir dönüş değerine sahip değilken oluşturulur. Bu, işleviyle aynı adla bir değerini örtülü `Set` yerel değişkene attırma içerir. Yeni projeler için varsayılan değer açıktır.

Kimlik: 42105 (işlev), 42016 (işleç)

### <a name="overloads-modifier-used-in-a-module-warning"></a>Modül uyarılarında kullanılan aşırı yükleme değiştiricisi
içinde `Overloads` kullanılırken `Module` oluşturulur. Yeni projeler için varsayılan değer açıktır.

Kimlik: 42028

### <a name="duplicate-or-overlapping-catch-blocks-warnings"></a>Yinelenen veya çakışan yakalama blokları uyarıları
Tanımlanmış diğer `Catch` bloklarla olan ilişkisi nedeniyle bir bloka hiçbir `Catch` zaman ulaşılamaysa oluşturulur. Yeni projeler için varsayılan değer açıktır.

Kimlik: 42029, 42031

## <a name="see-also"></a>Ayrıca bkz.

- [Hata türleri](/dotnet/visual-basic/programming-guide/language-features/error-types)
- [Deneyin... Yakalamak... Finally deyimi](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)
- [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn)
- [/warnaserror (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror)
- [Derleme sayfası, Project Tasarımcısı (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md)
- [Varsayılan olarak kapalı olan derleyici uyarıları](/cpp/preprocessor/compiler-warnings-that-are-off-by-default)
