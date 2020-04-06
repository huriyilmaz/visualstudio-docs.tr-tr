---
title: Kaynak Denetimi Entegrasyonuna Genel Bakış | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], about source control
ms.assetid: 3a46e4eb-e677-49c3-8647-d927d035a19a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d80363286f5f0cac9a5ceb2e8ac9d20345df9e6f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705118"
---
# <a name="source-control-integration-overview"></a>Kaynak Denetimini Tümleştirmeye Genel Bakış
Bu bölümde Visual Studio kaynak denetimine entegre etmek için iki yol karşılaştırır; bir kaynak denetimi Eklentisi ve kaynak kontrol çözümü sağlayan ve yeni kaynak kontrol özelliklerini vurgulayan bir VSPackage. Visual Studio, kaynak kontrolü VSPackages ve kaynak kontrol eklentileri arasında manuel geçiş inyanıtlarının yanı sıra otomatik çözüm tabanlı anahtarlama sağlar.

## <a name="source-control-integration"></a>Kaynak Denetimi Tümleştirmesi
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]iki tür kaynak denetimi tümleştirme seçeneğini destekler. Tüm [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]sürümlerinde, Visual Studio kaynak denetimi kullanıcı arabirimi (UI) kullanırken temel kaynak denetimi işlevselliği sağlayan Kaynak Denetimi Eklentisi API'sine (daha önce MSSCCI API olarak da adlandırılır) dayalı bir eklentiyi tümleştirebilirsiniz. Bir kaynak kontrolü VSPackage, diğer taraftan, kaynak kontrol [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] modelinde sofistike ve özerklik yüksek düzeyde gerektiren kaynak kontrol entegrasyonu için uygun yeni, derin entegrasyon yolu sağlar.

 ![Kaynak Denetimine Genel Bakış](../../extensibility/internals/media/sourcectnrloverview.gif "KaynakCtnrlOverview")

## <a name="source-control-plug-in"></a>Kaynak Kontrol Eklentisi
 Visual Studio'nun tüm sürümleri, kaynak denetimi eklentisi API belirtimi sürüm 1.2'yi tümleştirme yolu olarak destekler. Bir kaynak denetim eklentisi uygulayıcısı kaynak denetimi entegrasyonu ve kayıt için Kaynak Denetimi [Eklentisi](../../extensibility/internals/creating-a-source-control-plug-in.md)API işlevlerini uygulayan bir DLL yazar. Bu yaklaşımda, Tümleşik Geliştirme Ortamı [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (IDE), iade, kullanıma al, araçlar/seçenekler özellik sayfaları, araç çubukları ve kaynak denetimi glifleri gibi iletişim kutuları için Kullanıcı Arabirimi'ni kullanır. Kaynak Denetimi Eklentisi API'sine sıkı sıkıya bağlı kalmak Visual Studio'ya kolay bir entegrasyon ve kullanıcı için sorunsuz bir deneyim sağlar. Bu, kaynak denetim eklentisinin API'de ayrıntılı olarak belirtilen işlevlerin ve geri aramaların çoğunu uygulaması gerektiği anlamına gelir.

 Kaynak Denetimi Eklentisi API'sini kullanarak kaynak denetimi eklentisi uygulamak için aşağıdaki adımları izleyin:

1. [Kaynak Denetim Eklentilerinde](../../extensibility/source-control-plug-ins.md)belirtilen işlevleri uygulayan bir DLL oluşturun.

2. Uygun kayıt defteri girişlerini yaparak DLL'yi kaydedin [(Kaynak Denetim Eklentisi Yükleme) nasıl](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)açıklanmıştır.

3. Kaynak Denetim Bağdaştırıcı Paketi (kaynak kontrol eklentileri aracılığıyla kaynak denetimi işlevselliğini işleyen Visual Studio bileşeni) tarafından istendiğinde yardımcı bir arama aracı oluşturun ve görüntüle

   Bir kaynak denetim komutuna yanıt olarak, Visual Studio IDE temel işlemler için standart bir kullanıcı arabirimi sunar ve daha sonra bilgileri Kaynak Denetim Eklentisi API'sinde tanımlanan işlevler aracılığıyla kaynak denetim eklentisine aktarır. Gelişmiş seçenekler için, kaynak denetimi eklentisi, örneğin kaynak denetimli bir proje için tarama, kendi UI sunmak için çağrılabilir. Bu, kullanıcının kaynak denetimi yle uğraşırken kullanıcıya iki farklı kullanıcı stili sunulabileceği anlamına gelir: Visual Studio'nun sunduğu Kullanıcı ve kaynak denetimi eklentisinin sunduğu Kullanıcı Aracı. Bu en gelişmiş kaynak kontrol işlemleri ile fark edilir.

### <a name="drawbacks-to-implementing-a-source-control-plug-in"></a>Kaynak Kontrol Eklentisi Uygulamanın Sakıncaları

- Gelişmiş özellikler için, kullanıcı olası karışıklığa yol açan iki farklı arabirim stili görebilir.

- Kaynak denetim eklentisi, Kaynak Denetimi Eklentisi API'sinin ima ettiği kaynak denetim modeliyle sınırlıdır.

- Kaynak Denetimi Eklentisi API'si bazı kaynak denetim senaryoları için çok kısıtlayıcı olabilir.

### <a name="advantages-to-implementing-a-source-control-plug-in"></a>Kaynak Kontrol Eklentisi Uygulamanın Avantajları

- Visual Studio, kaynak denetim eklentisinin karmaşık olabilecek ui uygulamasına gerek kalmaması için tüm temel kaynak kontrol işlemleri için tüm UI'yi sağlar.

- Sıkı API nedeniyle, kaynak denetim eklentisi daha kapsamlı işlevsellik sağlamak için harici kaynak denetim programları ile kolayca etkileşime girebilirsiniz; Visual Studio, kaynak denetimi işlevinin nasıl gerçekleştirildiğini çok fazla önemsemez, yalnızca Kaynak Denetimi Eklentisi API'sine göre gerçekleştirilir.

- Bir kaynak denetimi eklentisi uygulamak, bir kaynak denetimi VSPackage daha kolaydır.

## <a name="source-control-vspackage"></a>Kaynak Kontrol VSPackage
 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]kaynak kontrol işlevselliği ve Visual Studio tarafından sağlanan kaynak kontrol kullanıcı arabiriminin tam değiştirme ile Visual Studio derin entegrasyon sağlar. Bir kaynak denetimi VSPackage Visual Studio kayıtlı ve kaynak kontrol işlevselliği sağlar. Birkaç kaynak denetimi VSPackages Visual Studio'ya kaydedilebilse de, bunlardan yalnızca biri aynı anda etkin olabilir. Bir kaynak kontrolü VSPackage aktif iken Visual Studio kaynak kontrol işlevselliği ve görünüm üzerinde tam kontrole sahiptir. Sisteme kaydedilebilecek diğer tüm kaynak denetimi VSPackages etkin değildir ve hiçbir Kullanıcı Aracı görüntülemez.

 Bir kaynak denetimi VSPackage uygulanması bir "ya hep ya hiç" stratejisi gerektirir. Bir kaynak denetimi VSPackage yaratıcısı tüm kaynak denetimi işlevselliğini kapsayacak şekilde kaynak denetim arabirimleri ve yeni UI öğeleri (iletişim kutuları, menüler ve araç çubukları) bir dizi uygulanması çaba önemli miktarda yatırım yapmalıdır. Daha fazla ayrıntı için [Kaynak Denetim VSPackage Oluşturma](../../extensibility/internals/creating-a-source-control-vspackage.md) konusuna bakın.

### <a name="drawbacks-to-implementing-a-source-control-vspackage"></a>Kaynak Kontrol VSPackage Uygulamanın Sakıncaları

- VSPackage Visual Studio ile başarılı bir şekilde entegre etmek için karmaşık arabirimler bir dizi uygulamak gerekir.

- VSPackage kaynak kontrolü için gerekli tüm UI sağlamalıdır; Visual Studio bu alanda hiçbir yardım sağlayacaktır.

- Bir kaynak kontrolü VSPackage yakından Visual Studio bağlı ve tek başına programları ile çalışamaz, bu nedenle işlevsellik kolayca kaynak kontrol programının harici bir sürümü ile paylaşılamaz.

### <a name="advantages-to-implementing-a-source-control-vspackage"></a>Kaynak Kontrol VSPackage Uygulama Avantajları

- VSPackage kaynak denetimi kullanıcı arabirimi ve işlevselliği üzerinde tam kontrole sahip olduğundan, kullanıcı kaynak denetimi için sorunsuz bir arayüz ile sunulur.

- VSPackage belirli bir kaynak kontrol modeli ile sınırlı değildir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi](../../extensibility/internals/source-control.md)
- [Kaynak Denetimi Eklentisi Oluşturma](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [Kaynak Denetimi VSPackage’ı Oluşturma](../../extensibility/internals/creating-a-source-control-vspackage.md)
- [Kaynak Denetimindeki Yenilikler](../../extensibility/internals/what-s-new-in-source-control.md)
