---
title: Visual Basic uyarı yapılandırma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- errors [Visual Basic], warnings
- run-time errors, warnings
- warnings, configuring
ms.assetid: 99cf4781-bd4d-47b4-91b9-217933509f82
caps.latest.revision: 37
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d09a251dc5f98080b317e1560423dcb7c8bf0805
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72619306"
---
# <a name="configuring-warnings-in-visual-basic"></a>Visual Basic'teki Uyarıları Yapılandırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]Derleyici, çalışma zamanı hatalarına neden olabilecek kodla ilgili bir uyarı kümesi içerir. Daha az hata ile temizleyici, daha hızlı ve daha iyi kod yazmak için bu bilgileri kullanabilirsiniz. Örneğin, Kullanıcı atanmamış bir nesne değişkeninin bir üyesini çağırmayı denediğinde bir uyarı oluşturur, dönüş değerini ayarlamadan bir işlevden geri dönüş veya `Try` özel durumları yakalamak için mantığdaki hatalarla bir blok yürütmez.

 Bazen derleyici Kullanıcı adına ek mantık sağlar, böylece Kullanıcı, benimsemeyi bekleme olası hatalar yerine her seferinde bir göreve odaklanabilir. Önceki sürümlerinde [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] , `Option Strict` derleyicinin sağladığı ek mantığı sınırlandırmak için kullanılmıştır [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] . Uyarıları yapılandırmak, bu mantığı bireysel uyarıların düzeyinde daha ayrıntılı bir şekilde sınırlamanıza olanak tanır.

 Projenizi özelleştirmek ve diğer uyarıları hatalara karşı yaparken uygulamanız için gerekli olan bazı uyarıları kapatmak isteyebilirsiniz. Bu sayfada, tek tek uyarıların nasıl kapatılacağı ve kapatılacağı açıklanmaktadır.

## <a name="turning-warnings-off-and-on"></a>Uyarıları kapatma ve açma
 Uyarıları yapılandırmanın iki farklı yolu vardır: **Proje tasarımcısını**kullanarak bunları yapılandırabilir veya **/warnaserror** ve **/nowarn** derleyici seçeneklerini kullanabilirsiniz.

 **Proje Tasarımcısı** sayfasının **Derle** sekmesi, uyarıları açıp kapatmanızı sağlar. Tüm uyarıları devre dışı bırakmak için **tüm uyarıları devre dışı bırak** onay kutusunu seçin; Tüm uyarıları hata olarak değerlendirmek için **tüm uyarıları hata olarak değerlendir** ' i seçin. Bazı ayrı uyarılar, görüntülenmiş tabloda istendiği gibi hata veya uyarı olarak değiştirilebilir.

 **Option Strict** **devre dışı**olarak ayarlandığında, kesin ilgili uyarı **seçeneği** birbirinden bağımsız olarak kabul edilemez. **Option Strict** **Açık**olarak ayarlandığında, ilişkili uyarılar, durumu ne olduğuna bakılmaksızın hata olarak değerlendirilir. **Option Strict** **Custom** `/optionstrict:custom` , komut satırı derleyicisinde belirtilerek özel olarak ayarlandığında, **kesin** uyarılar bağımsız olarak açık veya kapalı olabilir.

 Derleyicinin **/warnaserror** komut satırı seçeneği, uyarıların hata olarak değerlendirilip değerlendirilmeyeceğini belirtmek için de kullanılabilir. + Veya-kullanarak hangi uyarıların hata veya uyarı olarak değerlendirileceğini belirtmek için bu seçeneğe virgülle ayrılmış bir liste ekleyebilirsiniz. Aşağıdaki tabloda olası seçenekler ayrıntılı olarak verilmiştir.

|Komut satırı araçları|Belirler|
|--------------------------|---------------|
|`/warnaserror+`|Tüm uyarıları hata olarak değerlendir|
|`/warnsaserror`-|Hata olarak uyarı olarak davranmayın. Bu varsayılan seçenektir.|
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
 Örtük dönüştürme örnekleri için oluşturulur. İşleci kullanılırken, iç sayısal türden bir dizeye örtük dönüştürmeler eklemeyin `&` . Yeni projeler için varsayılan değer kapalıdır.

 KIMLIK: 42016

### <a name="late-bound-method-invocation-and-overload-resolution-warning"></a>Geç bağlantılı Yöntem çağırma ve aşırı yükleme çözümleme uyarısı
 Geç bağlama örnekleri için oluşturulur. Yeni projeler için varsayılan değer kapalıdır.

 KIMLIK: 42017

### <a name="operands-of-type-object-warnings"></a>Nesne uyarıları türündeki işlenenler
 Türünde `Object` bir hata oluşturacak tür işlenenleri oluştuğunda üretilir `Option Strict On` . Yeni projeler için varsayılan değer açık.

 KIMLIK: 42018 ve 42019

### <a name="declarations-require-as-clause-warnings"></a>Bildirimler ' As ' yan tümce uyarıları gerektirir
 Bir yan tümce olmayan bir değişken, işlev veya özellik bildirimi `As` ile bir hata oluşturacaksa oluşturulur `Option Strict On` . Kendisine atanmış bir türü olmayan değişkenlerin tür olduğu varsayılır `Object` . Yeni projeler için varsayılan değer açık.

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

### <a name="recursive-operator-or-property-access-warnings"></a>Özyinelemeli Işleç veya özellik erişimi uyarıları
 Bir yordamın gövdesi, içinde tanımlanan işleç veya özelliği kullandığında oluşturulur. Yeni projeler için varsayılan değer açık.

 KIMLIK: 42004 (işleç), 42026 (özellik)

### <a name="function-or-operator-without-return-value-warning"></a>Dönüş değeri olmayan işlev veya Işleç uyarısı
 İşlevin veya işlecin belirtilen bir dönüş değeri olmadığında üretilir. Bu, `Set` işlevle aynı ada sahip örtük yerel değişkene bir ile atlama içerir. Yeni projeler için varsayılan değer açık.

 KIMLIK: 42105 (işlev), 42016 (işleç)

### <a name="overloads-modifier-used-in-a-module-warning"></a>Modül uyarısında kullanılan aşırı yükleme değiştiricisi
 `Overloads`Bir içinde kullanıldığında oluşturulur `Module` . Yeni projeler için varsayılan değer açık.

 KIMLIK: 42028

### <a name="duplicate-or-overlapping-catch-blocks-warnings"></a>Yinelenen veya çakışan catch blokları uyarıları
 `Catch`Tanımlı diğer bloklarla ilişkili olduğundan hiçbir zaman bir bloğa ulaşılmadığında oluşturulur `Catch` . Yeni projeler için varsayılan değer açık.

 KIMLIK: 42029, 42031

## <a name="see-also"></a>Ayrıca Bkz.
 [Özel durum Yardımcısı Iletişim kutusu](../debugger/exception-assistant-dialog-box.md) [hata türleri](https://msdn.microsoft.com/library/3048aabf-8c97-4e13-9150-853769cb5f6f) [dene... Yakala... Finally ekstresi](https://msdn.microsoft.com/library/d6488026-ccb3-42b8-a810-0d97b9d6472b) [/nowarn](https://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83) [/warnaserror (Visual Basic)](https://msdn.microsoft.com/library/49819f1d-a1bd-4201-affe-5afe6d9712e1) [derleme sayfası, varsayılan olarak kapalı olan proje Tasarımcısı (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md) [derleyicisi uyarıları](https://msdn.microsoft.com/library/69809cfb-a38a-4035-b154-283a61938df8)
