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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114723"
---
# <a name="configuring-warnings-in-visual-basic"></a>Visual Basic'te uyarıları yapılandırma

Derleyici, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] çalışma zamanı hatalarına neden olabilecek kodla ilgili bir dizi uyarı içerir. Daha az hata ile daha temiz, daha hızlı, daha iyi kod yazmak için bu bilgileri kullanabilirsiniz. Örneğin, derleyici, kullanıcı atanmamış bir nesne değişkeninin üyesini çağırmaya, iade değerini ayarlamadan bir işlevden `Try` dönmeye veya özel durumları yakalamak için mantıkta hatalariçeren bir bloğu yürütmeye çalıştığında bir uyarı oluşturur.

Bazen derleyici, kullanıcının olası hataları tahmin etmek yerine eldeki göreve odaklanabilmesi için kullanıcı adına ekstra mantık sağlar. Derlemenin sağladığı [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]ek mantığı sınırlamak için , Option [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] **Strict'in** önceki sürümlerinde kullanılmıştır. Uyarıları yapılandırmak, bu mantığı tek tek uyarılar düzeyinde daha ayrıntılı bir şekilde sınırlamanızı sağlar.

Projenizi özelleştirmek ve diğer uyarıları hataya dönüştürürken uygulamanızla ilgili olmayan bazı uyarıları kapatmak isteyebilirsiniz. Bu sayfa, tek tek uyarıların nasıl açIlip kapatılabildiğini açıklar.

## <a name="turning-warnings-off-and-on"></a>Uyarıları kapatma ve açma
Uyarıları yapılandırmanın iki farklı yolu vardır: **Bunları Proje Tasarımcısı'nı**kullanarak yapılandırabilirsiniz veya **/warnaserror** ve **/nowarn** derleyici seçeneklerini kullanabilirsiniz.

**Proje Tasarımcısı** sayfasının **Derle** sekmesi uyarıları açıp kapatmanızı sağlar. Tüm uyarıları devre dışı kalmak için **Tüm Uyarıları Devre Dışı Atla** onay kutusunu seçin; tüm uyarıları hata olarak ele almak için **Tüm Uyarıları Hata Olarak Ele'i** seçin. Bazı bireysel uyarılar, görüntülenen tabloda istenildiği gibi hata veya uyarı olarak değiştirilebilir.

**Seçenek Katı** **Kapalı**ayarlandığında, **Seçenek Sıkı** ilgili uyarılar birbirinden bağımsız olarak tedavi edilemez. **Seçenek Katı** A.B.D. olarak ayarlandığında, ilişkili uyarılar durumları ne olursa olsun hata olarak kabul edilir. **On** **Option Strict** komut satırı derleyicisinde belirterek `/optionstrict:custom` **Özel** olarak ayarlandığında, **Seçenek Katı** uyarıları bağımsız olarak veya kapalı olarak değiştirilebilir.

Derleyicinin **/warnaserror** komut satırı seçeneği, uyarıların hata olarak kabul edilip edilmeyeceğini belirtmek için de kullanılabilir. Bu seçene, + veya -kullanarak hangi uyarıların hata veya uyarı olarak ele alınması gerektiğini belirtmek için virgül lesınırlı bir liste ekleyebilirsiniz. Aşağıdaki tabloda olası seçenekler ayrıntılı olarak anlatılır.

|Komut satırı araçları|Belirler|
| - |---------------|
|`/warnaserror+`|Tüm uyarıları hata olarak değerlendirin|
|`/warnsaserror`-|Uyarıları hata olarak ele alamayın. Bu varsayılandır.|
|`/warnaserror+:<warning list` `>`|Belirli uyarıları, virgülle sınırlandırılmış liste r'deki hata kimlik numarasına göre listelenen hatalar olarak değerlendirin.|
|`/warnaserror-:<warning list>`|Belirli uyarıları, virgülle sınırlandırılmış bir listede hata kimliği numarasına göre listelenen hatalar olarak ele almaz.|
|`/nowarn`|Uyarıları bildirmeyin.|
|`/nowarn:<warning list>`|Virgülle sınırlandırılmış lar listesinde hata kimlik numarasına göre listelenen belirtilen uyarıları bildirmeyin.|

Uyarı listesi, belirli uyarıları açmak veya kapatmak için komut satırı seçenekleriyle kullanılabilen hata olarak kabul edilmesi gereken uyarıların hata kimlik numaralarını içerir. Uyarı listesi geçersiz bir sayı içeriyorsa, bir hata bildirilir.

## <a name="examples"></a>Örnekler
Komut satırı bağımsız değişkenlerinin örnekleribu tablo, her bağımsız değişkenin ne yaptığını açıklar.

|Bağımsız Değişken|Açıklama|
|--------------|-----------------|
|`vbc /warnaserror`|Tüm uyarıların hata sayılması gerektiğini belirtir.|
|`vbc /warnaserror:42024`|42024 uyarısı bir hata olarak kabul edilmelidir belirtir.|
|`vbc /warnaserror:42024,42025`|42024 ve 42025 uyarılarının hata olarak ele alınması gerektiğini belirtir.|
|`vbc /nowarn`|Hiçbir uyarı bildirilmesi gerektiğini belirtir.|
|`vbc /nowarn:42024`|42024 uyarısı bildirilmemelidir.|
|`vbc /nowarn:42024,42025`|42024 ve 42025 uyarılarının bildirilmemesi gerektiğini belirtir.|

## <a name="types-of-warnings"></a>Uyarı türleri
Aşağıda, hata olarak ele almak isteyebileceğiniz uyarıların bir listesi verilmiştir.

### <a name="implicit-conversion-warning"></a>Örtük dönüştürme uyarısı
Örtülü dönüştürme örnekleri için oluşturulur. `&` İşleç kullanırken içsel sayısal türden bir dize örtük dönüşümleri içermezler. Yeni projeler için varsayılan değer kapalıdır.

Kimlik Numarası: 42016

### <a name="late-bound-method-invocation-and-overload-resolution-warning"></a>Geç bağlı yöntem çağırma ve aşırı yük çözünürlüğü uyarısı
Geç bağlama örnekleri için oluşturulur. Yeni projeler için varsayılan değer kapalıdır.

Kimlik Numarası: 42017

### <a name="operands-of-type-object-warnings"></a>'Nesne' uyarılarının operands
**Seçenek Katı Açık'ta** `Object` bir hata oluşturacak tür operands oluştuğunda oluşturulan. Yeni projeler için varsayılan değer açıktır.

Kimlik Numarası: 42018 ve 42019

### <a name="declarations-require-as-clause-warnings"></a>Bildirimler 'As' yan tümcesi uyarıları gerektirir
`As` Bir yan tümcesi olmayan bir değişken, işlev veya özellik **bildirimi, Katı Seçenek Açık'ta**bir hata oluşturmuş sayılsa oluşturulur. Kendilerine atanmış bir türü olmayan değişkenlerin türü `Object`olduğu varsayılır. Yeni projeler için varsayılan değer açıktır.

ID: 42020 (değişken beyan), 42021 (fonksiyon bildirimi) ve 42022 (özellik bildirimi).

### <a name="possible-null-reference-exception-warnings"></a>Olası null referans özel durum uyarıları
Bir değer atanmadan önce bir değişken kullanıldığında oluşturulur. Yeni projeler için varsayılan değer açıktır.

Kimlik Numarası: 42104, 42030

### <a name="unused-local-variable-warning"></a>Kullanılmayan yerel değişken uyarısı
Yerel bir değişken bildirildiğinde ancak hiç atıfta bulunulmadığunda oluşturulur. Varsayılan değer açıktır.

Kimlik Numarası: 42024

### <a name="access-of-shared-member-through-instance-variable-warning"></a>Örnek değişken uyarısı ile paylaşılan üyenin erişimi
Paylaşılan bir üyeye bir örnek aracılığıyla erişirken oluşturulan yan etkiler olabilir veya paylaşılan bir üyeye bir örnek değişkeni üzerinden erişme ifadesinin sağ tarafı değildir veya parametre olarak geçiriliyor. Yeni projeler için varsayılan değer açıktır.

Kimlik Numarası: 42025

### <a name="recursive-operator-or-property-access-warnings"></a>Özyinelemeli operatör veya özellik erişim uyarıları
Bir yordamın gövdesi tanımlandığı işleç veya özelliği kullandığında oluşturulur. Yeni projeler için varsayılan değer açıktır.

ID: 42004 (operatör), 42026 (özellik)

### <a name="function-or-operator-without-return-value-warning"></a>İade değeri uyarısı olmadan işlev veya işleç
İşlev veya işleci belirtilen bir iade değeri yoksa oluşturulur. Bu, işleçle `Set` aynı ada sahip örtülü yerel değişkene bir atlayıp içerir. Yeni projeler için varsayılan değer açıktır.

ID: 42105 (fonksiyon), 42016 (operatör)

### <a name="overloads-modifier-used-in-a-module-warning"></a>Modül uyarısında kullanılan aşırı yükleyici
`Overloads` Bir `Module`' de kullanıldığında oluşturulur. Yeni projeler için varsayılan değer açıktır.

Kimlik Numarası: 42028

### <a name="duplicate-or-overlapping-catch-blocks-warnings"></a>Yinelenen veya çakışan yakalama blokları uyarıları
Tanımlanan diğer `Catch` `Catch` bloklar ile ilişkisi nedeniyle bir bloka hiçbir zaman ulaşılamediğinde oluşturulur. Yeni projeler için varsayılan değer açıktır.

Kimlik Numarası: 42029, 42031

## <a name="see-also"></a>Ayrıca bkz.

- [Hata türleri](/dotnet/visual-basic/programming-guide/language-features/error-types)
- [Deneyin... Yakalamak... Son olarak deyimi](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)
- [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn)
- [/warnaserror (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror)
- [Derleme sayfası, Proje Tasarımcısı (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md)
- [Varsayılan olarak kapalı olan derleyici uyarıları](/cpp/preprocessor/compiler-warnings-that-are-off-by-default)
