---
title: Visual Basic'teki Uyarıları Yapılandırma
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- errors [Visual Basic], warnings
- run-time errors, warnings
- warnings, configuring
ms.assetid: 99cf4781-bd4d-47b4-91b9-217933509f82
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 33302a4a686d80621cc64ee018371a2d03ea30ee
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114723"
---
# <a name="configuring-warnings-in-visual-basic"></a>Visual Basic uyarıları yapılandırma

[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] derleyicisi, çalışma zamanı hatalarına neden olabilecek kodla ilgili bir uyarı kümesi içerir. Daha az hata ile temizleyici, daha hızlı ve daha iyi kod yazmak için bu bilgileri kullanabilirsiniz. Örneğin, Kullanıcı atanmamış bir nesne değişkeninin bir üyesini çağırmayı denediğinde bir uyarı üretir, dönüş değerini ayarlamadan bir işlevden geri dönüş veya özel durumları yakalamak için mantığdaki hatalarla birlikte `Try` bir blok yürütmez.

Bazen derleyici Kullanıcı adına ek mantık sağlar, böylece Kullanıcı, benimsemeyi bekleme olası hatalar yerine her seferinde bir göreve odaklanabilir. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]önceki sürümlerinde, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] derleyicinin sağladığı ek mantığı sınırlamak için **Strict seçeneği** kullanılmıştır. Uyarıları yapılandırmak, bu mantığı bireysel uyarıların düzeyinde daha ayrıntılı bir şekilde sınırlamanıza olanak tanır.

Projenizi özelleştirmek ve diğer uyarıları hatalara karşı yaparken uygulamanız için gerekli olan bazı uyarıları kapatmak isteyebilirsiniz. Bu sayfada, tek tek uyarıların nasıl kapatılacağı ve kapatılacağı açıklanmaktadır.

## <a name="turning-warnings-off-and-on"></a>Uyarıları kapatma ve açma
Uyarıları yapılandırmanın iki farklı yolu vardır: **Proje tasarımcısını**kullanarak bunları yapılandırabilir veya **/warnaserror** ve **/nowarn** derleyici seçeneklerini kullanabilirsiniz.

**Proje Tasarımcısı** sayfasının **Derle** sekmesi, uyarıları açıp kapatmanızı sağlar. Tüm uyarıları devre dışı bırakmak için **tüm uyarıları devre dışı bırak** onay kutusunu seçin; Tüm uyarıları hata olarak değerlendirmek için **tüm uyarıları hata olarak değerlendir** ' i seçin. Bazı ayrı uyarılar, görüntülenmiş tabloda istendiği gibi hata veya uyarı olarak değiştirilebilir.

**Option Strict** **devre dışı**olarak ayarlandığında, kesin ilgili uyarı **seçeneği** birbirinden bağımsız olarak kabul edilemez. **Option Strict** **Açık**olarak ayarlandığında, ilişkili uyarılar, durumu ne olduğuna bakılmaksızın hata olarak değerlendirilir. **Option Strict** , komut satırı derleyicisinde `/optionstrict:custom` belirterek **özel** olarak ayarlandığında, **kesin** uyarılar bağımsız olarak açık veya kapalı olabilir.

Derleyicinin **/warnaserror** komut satırı seçeneği, uyarıların hata olarak değerlendirilip değerlendirilmeyeceğini belirtmek için de kullanılabilir. \+ Veya-kullanarak hangi uyarıların hata veya uyarı olarak değerlendirileceğini belirtmek için bu seçeneğe virgülle ayrılmış bir liste ekleyebilirsiniz. Aşağıdaki tabloda olası seçenekler ayrıntılı olarak verilmiştir.

|Komut satırı seçeneği|Belirler|
| - |---------------|
|`/warnaserror+`|Tüm uyarıları hata olarak değerlendir|
|`/warnsaserror`-|Hata olarak uyarı olarak davranmayın. Bu varsayılandır.|
|`/warnaserror+:<warning list` `>`|Belirli uyarıları, virgülle ayrılmış bir liste r içinde kendi hata KIMLIĞI numarası ile listelenmiş hata olarak değerlendirin.|
|`/warnaserror-:<warning list>`|Belirli uyarıları hata olarak değerlendirmeyin ve hata KIMLIK numarası, virgülle ayrılmış bir liste ile listelenir.|
|`/nowarn`|Uyarı bildirme.|
|`/nowarn:<warning list>`|Belirtilen uyarıları, kendi hata KIMLIĞI numarasına göre, virgülle ayrılmış bir listede bildirmeyin.|

Uyarı listesi, belirli uyarıları açmak veya kapatmak için komut satırı seçenekleriyle kullanılabilecek, hata olarak değerlendirilmesi gereken uyarıların hata KIMLIĞI numaralarını içerir. Uyarı listesi geçersiz bir sayı içeriyorsa, bir hata bildirilir.

## <a name="examples"></a>Örnekler
Komut satırı bağımsız değişkenlerinin Bu örnek tablosu, her bir bağımsız değişkenin ne yaptığını açıklar.

|Bağımsız Değişken|Açıklama|
|--------------|-----------------|
|`vbc /warnaserror`|Tüm uyarıların hata sayılması gerektiğini belirtir.|
|`vbc /warnaserror:42024`|Uyarı 42024 ' nin hata olarak değerlendirilip değerlendirilmeyeceğini belirtir.|
|`vbc /warnaserror:42024,42025`|Uyarı 42024 ve 42025 ' nin hata olarak değerlendirilip değerlendirilmeyeceğini belirtir.|
|`vbc /nowarn`|Hiçbir uyarı raporlanmamalıdır.|
|`vbc /nowarn:42024`|Uyarı 42024 bildirilmemelidir.|
|`vbc /nowarn:42024,42025`|Uyarı 42024 ve 42025 ' nin bildirilmemelidir.|

## <a name="types-of-warnings"></a>Uyarı türleri
Hata olarak değerlendirmek isteyebileceğiniz uyarıların listesi aşağıda verilmiştir.

### <a name="implicit-conversion-warning"></a>Örtük dönüştürme uyarısı
Örtük dönüştürme örnekleri için oluşturulur. `&` işleci kullanılırken, iç sayısal türden bir dizeye örtük dönüştürmeler eklemeyin. Yeni projeler için varsayılan değer kapalıdır.

KIMLIK: 42016

### <a name="late-bound-method-invocation-and-overload-resolution-warning"></a>Geç bağlantılı Yöntem çağırma ve aşırı yükleme çözümleme uyarısı
Geç bağlama örnekleri için oluşturulur. Yeni projeler için varsayılan değer kapalıdır.

KIMLIK: 42017

### <a name="operands-of-type-object-warnings"></a>' Object ' uyarı türünde işlenenler
Tür işlenenleri `Object` oluştuğunda üretilir ve **Option Strict On**ile bir hata oluşturur. Yeni projeler için varsayılan değer açık.

KIMLIK: 42018 ve 42019

### <a name="declarations-require-as-clause-warnings"></a>Bildirimler ' As ' yan tümce uyarıları gerektirir
Bir `As` yan tümcesi bulunmayan bir değişken, işlev veya özellik bildirimi, **Option Strict On**ile bir hata oluşturacaksa üretilir. Kendisine atanmış bir türü olmayan değişkenlerin türü `Object`olarak kabul edilir. Yeni projeler için varsayılan değer açık.

KIMLIK: 42020 (değişken bildirimi), 42021 (işlev bildirimi) ve 42022 (özellik bildirimi).

### <a name="possible-null-reference-exception-warnings"></a>Olası boş başvuru özel durum uyarıları
Bir değere atanmadan önce bir değişken kullanıldığında oluşturulur. Yeni projeler için varsayılan değer açık.

KIMLIK: 42104, 42030

### <a name="unused-local-variable-warning"></a>Kullanılmayan yerel değişken uyarısı
Yerel bir değişken bildirildiği ancak hiçbir zaman başvurduğu zaman üretilir. Varsayılan değer açık.

KIMLIK: 42024

### <a name="access-of-shared-member-through-instance-variable-warning"></a>Örnek değişkeni aracılığıyla paylaşılan üyeye erişim Uyarısı
Bir örnek üzerinden paylaşılan bir üyeye erişilirken oluşturulan, yan etkileri olabilir veya bir örnek değişken aracılığıyla paylaşılan bir üyeye erişildiğinde bir ifadenin sağ tarafı değildir veya bir parametre olarak geçirilir. Yeni projeler için varsayılan değer açık.

KIMLIK: 42025

### <a name="recursive-operator-or-property-access-warnings"></a>Özyinelemeli işleç veya özellik erişimi uyarıları
Bir yordamın gövdesi, içinde tanımlanan işleç veya özelliği kullandığında oluşturulur. Yeni projeler için varsayılan değer açık.

KIMLIK: 42004 (işleç), 42026 (özellik)

### <a name="function-or-operator-without-return-value-warning"></a>Dönüş değeri olmayan işlev veya işleç uyarısı
İşlevin veya işlecin belirtilen bir dönüş değeri olmadığında üretilir. Bu, işlevle aynı ada sahip örtük yerel değişkene bir `Set` atlama içerir. Yeni projeler için varsayılan değer açık.

KIMLIK: 42105 (işlev), 42016 (işleç)

### <a name="overloads-modifier-used-in-a-module-warning"></a>Modül uyarısında kullanılan aşırı yükleme değiştiricisi
Bir `Module``Overloads` kullanıldığında oluşturulur. Yeni projeler için varsayılan değer açık.

KIMLIK: 42028

### <a name="duplicate-or-overlapping-catch-blocks-warnings"></a>Yinelenen veya çakışan catch blokları uyarıları
Tanımlı diğer `Catch` bloklarıyla ilişkili olduğundan `Catch` bloğuna hiçbir zaman ulaşılmadığında oluşturulur. Yeni projeler için varsayılan değer açık.

KIMLIK: 42029, 42031

## <a name="see-also"></a>Ayrıca bkz.

- [Hata türleri](/dotnet/visual-basic/programming-guide/language-features/error-types)
- [Deneyin... Yakala... Finally ekstresi](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)
- [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn)
- [/warnaserror (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror)
- [Derleme sayfası, proje Tasarımcısı (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md)
- [Varsayılan olarak kapalı olan Derleyici Uyarıları](/cpp/preprocessor/compiler-warnings-that-are-off-by-default)
