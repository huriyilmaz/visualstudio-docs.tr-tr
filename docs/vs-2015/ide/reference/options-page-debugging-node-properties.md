---
title: Seçenekler sayfası, hata ayıklama düğümü özellikleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 564cc8b2-0084-420e-b560-200cc5621a7e
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 10537fb64e6ae0ebbe185024b76442704437e273
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668836"
---
# <a name="options-page-debugging-node-properties"></a>Seçenekler Sayfası, Hata Ayıklama Düğümü Özellikleri
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Aşağıdaki tablolarda, Seçenekler iletişim kutusunun **hata ayıklama** kategorisiyle ilişkili sayfalar (veya özellikler koleksiyonlar) açıklanır `DTE.Properties("Debugging", <Property Page>)` . **Options**

## <a name="general"></a>Genel
 `DTE.Properties("Debugging", "General")`

|Özellik Öğesi Adı|Değer|Açıklama|
|------------------------|-----------|-----------------|
|PromptOnBreakpointDelete|Get/Set (Boole)|Hata ayıklayıcının bir projedeki tüm kesme noktalarını silmeden önce izin isteyip istemeyeceğini belirler.|
|Breakkallprocesses|Get/Set (Boole)|Tek bir işlem kesildiğinde hata ayıklayıcının tüm işlemleri kesip bölmeyeceğini belirler.|
|Ayırıcı sınırları|Get/Set (Boole)|Bir özel durum AppDomain veya yönetilen ve yerel kod arasında bir kenarlığı aştığında hata ayıklayıcının yürütmeyi kesmesinin kesilmeyeceğini belirler.|
|EnableAddressLevelDebugging|Get/Set (Boole)|Adres düzeyi hata ayıklama özelliklerinin etkinleştirilip etkinleştirilmediğini belirler.|
|ShowDisassemblyIfNoSource|Get/Set (Boole)|Kaynak kodu kullanılabilir olmadığında hata ayıklayıcının ayrıştırılmış kodu görüntüleyip görüntülemediğini belirler.|
|EnableBreakpointFilters|Get/Set (Boole)|Kesme noktası filtrelemesinin etkinleştirilip etkinleştirilmeyeceğini belirler.|
|EnableExceptionAssistant|Get/Set (Boole)|Özel durum Yardımcısı 'Nın yönetilen özel durumlar için kullanılıp kullanılmayacağını belirler.|
|Unwınbir Callstack|Get/Set (Boole)|Hata ayıklayıcının işlenmeyen bir özel durum için çağrı yığınını geri kullanıp kullanmadığını belirler.|
|Enableadatmycode|Get/Set (Boole)|Yalnızca kendi kodum C# ve Visual Basic kodu için etkinleştirilip etkinleştirilmeyeceğini belirler.|
|ShowAllMembers|Get/Set (Boole)|Kullanıcı olmayan nesneler için, hata ayıklayıcının tüm nesne üyelerini değişkenler penceresinde görüntüleyip görüntülemediğini belirler. Yalnızca kendi kodum etkinleştirilmediği takdirde bu seçeneğin hiçbir etkisi yoktur.|
|WarnIfNoUserCode|Get/Set (Boole)|Kullanıcı, Kullanıcı kodu olmayan bir işleme iliştirmeye çalıştığında hata ayıklayıcının bir uyarı yayıp yaymayacağını belirler. Yalnızca kendi kodum etkinleştirilmediği takdirde bu seçeneğin hiçbir etkisi yoktur.|
|Enablepropertyedeğerleme|Get/Set (Boole)|Hata ayıklayıcının Yönetilen koddaki özellikleri ve örtük işlev çağrılarını otomatik olarak değerlendirme yapılıp yapılmayacağını belirler.|
|CallStringConversion|Get/Set (Boole)|Hata ayıklayıcının, değişkenler penceresinde nesnelerde bir dize dönüştürme işlevini örtülü olarak çağırmayacağını belirler. Bu seçenek yalnızca C# ve JScript kodu için geçerlidir.|
|EnableSourceServer|Get/Set (Boole)|Hata ayıklayıcının bir kaynak sunucudan koda erişip erişemeyeceğini belirler.|
|PrintSourceServerDiagnostics|Get/Set (Boole)|Çıkış penceresinin, kaynak sunucuyla ilgili tanılama iletilerini gösterilip gösterilmeyeceğini belirler. Kaynak sunucu erişimi etkinleştirilmediği takdirde bu seçeneğin hiçbir etkisi yoktur.|
|HighlightEntireLine|Get/Set (Boole)|Hata ayıklayıcının kesme noktaları ve geçerli ifade için bir satırın tamamını vurgulamayabileceğini belirler.|
|RequireSourceToMatch|Get/Set (Boole)|Hata ayıklama için dosyaları açtığınızda hata ayıklayıcının kaynak dosyaların özgün sürümle tam olarak eşleşip engellenmeyeceğini gerektirip gerektirmediğini belirler.|
|RedirectOutputToImmediate|Get/Set (Boole)|Çıkış penceresi çıktısının hemen pencereye yönlendirilip yönlendirilmeyeceğini belirler.|
|Showrawvariableyapısı|Get/Set (Boole)|Değişkenler pencerelerinin içindeki nesnelerin ham biçimde gösterilip gösterilmeyeceğini belirler.|
|Suppressjitoptılama|Get/Set (Boole)|Yönetilen kod için, hata ayıklayıcı tarafından tam zamanında iyileştirme 'nin bastırılmadığını belirler.|
|WarnIfNoSymbols|Get/Set (Boole)|İşlem başlatıldığında hata ayıklama sembolleri yoksa hata ayıklayıcının bir uyarı görüntüleyip görüntülemediğini belirler.|
|WarnIfScriptDisabled|Get/Set (Boole)|Bir işlem başlatıldığında betik hata ayıklaması etkinleştirilmemişse hata ayıklayıcının bir uyarı görüntüleyip görüntülemediğini belirler.|
|ShowMarkersForAllThreads|Get/Set (Boole)|Hata ayıklayıcının iş parçacığı işaretçilerini görüntüleyip görüntülemediğini belirler.|
|Stepoverpropertiesaniators|Get/Set (Boole)|Yalnızca yönetilen koddaki Özellikler ve işleçler üzerinde adımın yapılıp yapılmayacağını belirtir.|

## <a name="edit-and-continue"></a>Düzenle ve Devam Et
 `DTE.Properties("Debugging", "EditAndContinue")`

|Özellik Öğesi Adı|Değer|Açıklama|
|------------------------|-----------|-----------------|
|EnableEditAndContinue|Get/Set (Boole)|Düzenle ve devam et özelliğinin etkinleştirilip etkinleştirilmediğini belirler. Bu seçenek, Düzenle ve devam et 'i destekleyen tüm diller için geçerlidir.|
|Inkedbycommands|Get/Set (Boole)|Kullanıcı **Step** veya **Continue**gibi bir hata ayıklama komutu seçtiğinde düzenleme ve devam etmeyi otomatik olarak kod değişikliği uygulanıp uygulamadığını belirler. Bu seçenek yalnızca yerel kod için geçerlidir.|
|Inkedbycommandsaskfirst|Get/Set (Boole)|Düzenle ve devam et işlevi, Kullanıcı **adım** veya **devam et**gibi bir hata ayıklama komutu seçtiğinde, kullanıcıdan kod değişikliklerini uygulama izni isteyip istemeyeceğini belirler. Bu seçenek yalnızca yerel kod için geçerlidir.|
|Warnai Stalecode|Get/Set (Boole)|Düzenleme ve devam etme sırasında hata ayıklayıcının bir uyarı iletisi verip etmediğini belirler, güncel olmayan veya eski kodların yürütülmesine neden olur. Bu seçenek yalnızca yerel kod için geçerlidir.|
|RelinkChangesOnStop|Al/ayarla (kısa)|Visual Studio 'nun, uygulamanın yürütülmesi durdurulduğunda Düzenle ve devam et tarafından uygulanan kod değişikliklerinin yeniden oluşturulup oluşturulmayacağını belirler. Bu seçenek yalnızca yerel kod için geçerlidir.|
|Allowprederlemesini yapılandırma|Al/ayarla (kısa)|Düzenle ve devam et 'in arka planda önceden derlenmiş üstbilgileri yüklemesine izin verilip verilmeyeceğini belirler. Bu seçenek yalnızca yerel kod için geçerlidir.|

## <a name="just-in-time"></a>Tam Zamanında
 `DTE.Properties("Debugging", "JustInTime")`

|Özellik Öğesi Adı|Değer|Açıklama|
|------------------------|-----------|-----------------|
|Jyönetilen|Get/Set (Boole)|Yönetilen kod için tam zamanında hata ayıklamanın etkinleştirilip etkinleştirilmeyeceğini belirler.|
|Jyerel|Get/Set (Boole)|Yerel kod için tam zamanında hata ayıklamanın etkinleştirilip etkinleştirilmeyeceğini belirler.|
|JSCRIPT|Get/Set (Boole)|Betik kodu için tam zamanında hata ayıklamanın etkinleştirilip etkinleştirilmeyeceğini belirler.|

## <a name="native"></a>Yerel
 `DTE.Properties("Debugging", "Native")`

|Özellik Öğesi Adı|Değer|Açıklama|
|------------------------|-----------|-----------------|
|LoadDllExports|Get/Set (Boole)|Hata ayıklayıcının DLL dışa aktarma tablolarını yükleyip yüklemeyeceğini belirler.|
|EnableRPC|Get/Set (Boole)|Hata ayıklayıcının COM uzak yordam çağrılarına erişip erişemeyeceğini belirler.|

## <a name="see-also"></a>Ayrıca Bkz.
 Seçenekler sayfa seçenekleri sayfasında [özellik öğelerinin adlarını belirleyen](https://msdn.microsoft.com/library/d450422d-47c7-4eeb-9f9f-3286264bc5aa) [seçenek ayarlarını denetleme](https://msdn.microsoft.com/library/a09ed242-7494-4cde-bbd1-7a8ec617965d) [sayfası, yazı tipleri ve renkler düğüm özellikleri](../../ide/reference/options-page-fonts-and-colors-node-properties.md) [Seçenekler sayfası, metin düzenleyici düğümü özellikleri](../../ide/reference/options-page-text-editor-node-properties.md) [Genel, hata ayıklama, Seçenekler iletişim kutusu](../../debugger/general-debugging-options-dialog-box.md) [düzenleme ve devam etme](https://msdn.microsoft.com/library/009d225f-ef65-463f-a146-e4c518f86103) , hata ayıklama, Seçenekler iletişim kutusu [tam zamanında, hata ayıklama, Seçenekler iletişim kutusu](../../debugger/just-in-time-debugging-options-dialog-box.md)
