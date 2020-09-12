---
title: Kaynak denetimi eklentisinin en iyi yöntemlerini uygulama
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, best practices
- best practices, source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: 85e73b73-29dc-464f-8734-ed308742c435
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 399afaff75b2456e668aaa9862fb7aa5439cc39f
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90038458"
---
# <a name="best-practices-for-implementing-a-source-control-plug-in"></a>Kaynak denetim eklentisi uygulamak için en iyi uygulamalar
Aşağıdaki teknik ayrıntılar, ' de bir kaynak denetimi eklentisini güvenilir bir şekilde uygulamanıza yardımcı olabilir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

## <a name="memory-management-issues"></a>Bellek yönetimi sorunları
 Çoğu durumda, çağıran, bellek oluşturan ve ayıran tümleşik geliştirme ortamı (IDE). Kaynak denetimi eklentisi, dizeleri ve diğer öğeleri çağıran ayrılmış arabellekler halinde döndürür. Özel durumlar, oluşan belirli işlevlerin açıklamalarında belirtilmiştir.

## <a name="arrays-of-file-names"></a>Dosya adı dizileri
 Bir dizi dosya geçirildiğinde, bu dosya adı bitişik bir dizi olarak geçirilir. Dosya adlarına işaretçiler dizisi olarak geçirilir. Örneğin, [SccGet](../extensibility/sccget-function.md)içinde, dosya adları parametresi tarafından geçirilir `lpFileNames` ; burada `lpFileNames` aslında bir işaretçisidir `char **` . `lpFileNames`[0], ilk adın bir işaretçisidir, `lpFileNames` [1] ikinci ada bir işaretçidir ve bu şekilde devam eder.

## <a name="large-model"></a>Büyük model
 Tüm işaretçiler, 16 bit işletim sistemlerinde bile 32 bittir.

## <a name="fully-qualified-paths"></a>Tam olarak nitelenmiş yollar
 Dosya adları veya dizinleri bağımsız değişkenler olarak belirtildiğinde, ters eğik çizgiler olmadan tam olarak nitelenmiş yollar veya UNC yolları olmalıdır. Bu, temel kaynak denetim sisteminin bir gereksinimidir, bunları göreli yollara çevirecek kaynak denetimi eklentisinin sorumluluğundadır.

## <a name="specify-a-fully-qualified-path-for-the-registered-dll"></a>Kayıtlı DLL için tam olarak nitelenmiş bir yol belirtin
 IDE artık göreli yollardan dll 'Leri yüklemez (örneğin, *.\NewProvider.dll*). DLL 'nin tam yolu belirtilmelidir (örneğin, *C:\Providers\NewProvider.dll*). Bu gereksinim, yetkisiz veya kimliğine bürünülen kaynak denetimi DLL 'Lerinin yüklenmesini önleyecek şekilde IDE güvenliğini güçlendirir.

## <a name="check-for-an-existing-vssci-plug-in-when-you-install-your-source-control-plug-in"></a>Kaynak denetimi eklentisini yüklerken mevcut bir VSSCı eklentisini denetleyin
 Kaynak denetimi eklentiye yüklemeyi planlayan bir Kullanıcı, zaten bilgisayarda yüklü olan bir kaynak denetim eklentisine sahip olabilir. Oluşturduğunuz eklentiye yönelik yükleme (Kurulum) programı ilgili kayıt defteri anahtarları için mevcut değerler olup olmadığını belirlemelidir. Bu anahtarlar zaten ayarlandıysa, yükleme programınız, eklentiyi varsayılan kaynak denetimi eklentisi olarak kaydetmenizi ve zaten yüklü olan birini değiştirmesini ister.

## <a name="error-result-codes-and-reporting"></a>Hata sonuç kodları ve raporlama
 `SCC_OK`Bir kaynak denetimi işlevi için dönüş kodu, işlemin tüm dosyalar için başarılı olduğunu gösterir. İşlem başarısız olursa, karşılaşılan son hata kodunu döndürmesi beklenir.

 Raporlama kuralı, IDE 'de bir hata oluşursa IDE 'nin bunu bildirmekten sorumludur. Kaynak denetim sisteminde bir hata oluşursa, kaynak denetimi eklentisi onu raporlamadan sorumludur. Örneğin, **Şu anda hiçbir dosya seçili** değil IDE tarafından **bildirilmiyor ancak bu dosya zaten kullanıma alındı** , eklenti tarafından raporlanacaktır.

## <a name="the-context-structure"></a>Bağlam yapısı
 [SccInitialize](../extensibility/sccinitialize-function.md)çağrısı sırasında, çağıran, `ppvContext` başlatılmamış bir tanıtıcı olan parametreyi, void olan parametresini geçirir. Kaynak denetimi eklentisi bu parametreyi yok sayabilir veya herhangi bir türde yapıyı ayırabilir ve geçirilen işaretçiye bu yapıya bir işaretçi koyabilir. IDE bu yapıyı anlamaz, ancak bu yapıya bir işaretçi, eklentisindeki diğer her çağrıya geçirir. Bu, genel değişkenler kullanılmadan işlev çağrılarında sürekli olarak devam eden genel durum bilgilerini korumak için kullanabileceğiniz eklentiye yönelik değerli bağlam önbelleği bilgilerini sağlar. Eklenti, [Sccunınitialize](../extensibility/sccuninitialize-function.md)çağrısında yapıyı boşaltmaktan sorumludur.

 Eklenti, `SCC_CAP_REENTRANT` [SccInitialize](../extensibility/sccinitialize-function.md) (özellikle, parametresinde) bitini ayarlarsa `lpSccCaps` , açık olan tüm projeleri izlemek için birden çok bağlam yapısı kullanılır.

## <a name="bitflags-and-other-command-options"></a>Bitflags ve diğer komut seçenekleri
 [SccGet](../extensibility/sccget-function.md)gibi her komut için IDE, komutun davranışını değiştiren birçok seçenek belirtebilir.

 API, parametresi aracılığıyla IDE tarafından belirli seçeneklerin ayarını destekler `fOptions` . Bu seçenekler, belirli komutlar tarafından, etkilediği komutlarla birlikte [kullanılan Bitflags](../extensibility/bitflags-used-by-specific-commands.md) ile açıklanmıştır. Genel olarak, bunlar kullanıcıdan sorulmayacak seçeneklerdir.

 Çoğu kullanıcı yapılandırılabilir ayar seçeneği, kaynak denetimi eklentileri arasında çok büyük farklılıklar olduğu için bu şekilde tanımlanmamıştır. Bu nedenle, önerilen mekanizma **Gelişmiş** bir düğmedir. Örneğin, **Get** ILETIŞIM kutusunda IDE yalnızca anladığı bilgileri görüntüler, ancak eklentinin bu komut için seçenekleri varsa **Gelişmiş** bir düğme de görüntüler. Kullanıcı **Gelişmiş** düğmesine TıKLADıĞıNDA, IDE, kaynak denetimi eklentisinin bit bayrakları veya tarih/saat gibi bilgileri kullanıcıya sormasını sağlamak Için [Sccgetcommandotıı](../extensibility/sccgetcommandoptions-function.md) çağırır. Eklenti, bu bilgileri komut sırasında geri geçirilmiş bir yapıda döndürür `SccGet` .

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi eklentileri](../extensibility/source-control-plug-ins.md)
- [Kaynak denetimi eklentisi oluşturma](../extensibility/internals/creating-a-source-control-plug-in.md)
