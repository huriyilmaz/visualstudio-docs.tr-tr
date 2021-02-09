---
title: Kaynak denetimi tümleştirmesine genel bakış | Microsoft Docs
description: 'Kaynak denetimini Visual Studio ile tümleştirmenin iki yolu arasındaki farklar hakkında bilgi edinin: kaynak denetimi eklentisi ve VSPackage.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], about source control
ms.assetid: 3a46e4eb-e677-49c3-8647-d927d035a19a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7f3b0ddf956c3f5c2ec2fe51163b52f2a7a973aa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99846432"
---
# <a name="source-control-integration-overview"></a>Kaynak Denetimini Tümleştirmeye Genel Bakış
Bu bölüm, Visual Studio kaynak denetimiyle tümleştirmenin iki yolunu karşılaştırır; Kaynak denetimi eklentisi ve kaynak denetim çözümü sağlayan ve yeni kaynak denetimi özelliklerini vurgulayan bir VSPackage. Visual Studio, kaynak denetimi VSPackages ve kaynak denetimi eklentilerinin yanı sıra otomatik çözüm tabanlı geçiş arasında el ile geçiş yapılmasına imkan tanır.

## <a name="source-control-integration"></a>Kaynak Denetimi Tümleştirmesi
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] iki tür kaynak denetimi tümleştirme seçeneğini destekler. Tüm sürümlerinde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , Visual Studio kaynak denetimi kullanıcı arabirimi (UI) kullanırken temel kaynak denetimi işlevselliği sağlayan kaynak denetimi eklentisi API 'sine (daha önce de MSSCCı API 'si olarak da bilinir) bağlı olarak bir eklentiyi tümleştirmeye devam edebilirsiniz. Diğer yandan bir kaynak denetimi VSPackage, kaynak denetimi [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] modelinde yüksek düzeyde gelişmiş algoritmaların mümkündür ve bağımsız çalışma sınırı talep eden kaynak denetimi tümleştirmesi için uygun olan yeni ve derin tümleştirme yolu sağlar.

 ![Kaynak denetimine genel bakış](../../extensibility/internals/media/sourcectnrloverview.gif "SourceCtnrlOverview")

## <a name="source-control-plug-in"></a>Kaynak denetimi eklentisi
 Visual Studio 'nun tüm sürümleri, kaynak denetimi eklentisi API 'SI belirtim sürüm 1,2 ' i tümleştirme yolu olarak destekler. Kaynak denetimi eklentisi uygulayıcısı, kaynak denetimi eklentisi [oluşturma](../../extensibility/internals/creating-a-source-control-plug-in.md)bölümünde açıklandığı gibi kaynak denetimi tümleştirmesi ve kaydı Için kaynak denetimi eklentisi API işlevlerini uygulayan bir dll 'yi yazar. Bu yaklaşımda, tümleşik geliştirme ortamı (IDE), [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] iade etme, kullanıma alma, Araçlar/Seçenekler özellik sayfaları, araç çubukları ve kaynak denetim glifleri gibi iletişim kutuları için Kullanıcı arabirimini kullanır. Kaynak denetimi eklentisi API 'SI, Visual Studio 'ya kolay bir tümleştirme ve Kullanıcı için sorun içermeyen bir deneyim yöntem. Bu, kaynak denetimi eklentisinin API 'de ayrıntılanmış işlevlerin ve geri aramaların çoğunu uygulaması gereken anlamına gelir.

 Kaynak denetimi eklentisi API 'sini kullanarak bir kaynak denetimi eklentisi uygulamak için aşağıdaki adımları izleyin:

1. [Kaynak denetimi eklentilerinde](../../extensibility/source-control-plug-ins.md)belirtilen işlevleri uygulayan bir DLL oluşturun.

2. Uygun kayıt defteri girdilerini ( [nasıl yapılır: kaynak denetimi eklentisi yüklemesi](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)) yaparak dll 'yi kaydettirin.

3. Bir yardımcı Kullanıcı arabirimi oluşturun ve kaynak denetim bağdaştırıcısı paketi (kaynak denetimi eklentileri aracılığıyla kaynak denetimi işlevini işleyen Visual Studio bileşeni) istendiğinde görüntüleyin

   Kaynak denetim komutuna yanıt olarak, Visual Studio IDE temel işlemler için standart bir kullanıcı arabirimi sunar ve ardından kaynak denetimi eklentisi API 'sinde tanımlanan işlevler aracılığıyla bilgileri kaynak denetimi eklentisine geçirir. Gelişmiş seçenekler için, kaynak denetimi eklentisi, kendi Kullanıcı arabirimini sunmak için üzerinde çağrılabilir, örneğin, kaynak denetimli bir projeye göz atma. Bu, kullanıcının kaynak denetimiyle ilgilenirken büyük olasılıkla farklı kullanıcı ARABIRIMI stilleriyle sunulabileceği anlamına gelir: Visual Studio 'nun sunduğu Kullanıcı arabirimi ve kaynak denetimi eklentisinin sunduğu Kullanıcı arabirimi. Bu, gelişmiş kaynak denetimi işlemleriyle en belirgin şekilde görülür.

### <a name="drawbacks-to-implementing-a-source-control-plug-in"></a>Kaynak denetimi eklentisi uygulama dezavantajları

- Gelişmiş özellikler için Kullanıcı, olası karışıklıklara neden olacak şekilde iki farklı arabirim stili görebilir.

- Kaynak denetimi eklentisi, kaynak denetimi eklentisi API 'SI tarafından belirtilen kaynak denetim modeliyle sınırlandırmış.

- Kaynak denetimi eklentisi API 'SI bazı kaynak denetim senaryolarında çok kısıtlayıcı olabilir.

### <a name="advantages-to-implementing-a-source-control-plug-in"></a>Kaynak denetimi eklentisi uygulama avantajları

- Visual Studio tüm temel kaynak denetim işlemlerine yönelik tüm Kullanıcı arabirimini sağlar, böylece kaynak denetimi eklentisi potansiyel olarak karmaşık kullanıcı arabirimini uygulamak zorunda değildir.

- Katı API sayesinde, kaynak denetimi eklentisi daha kapsamlı işlevsellik sağlamak için dış kaynak denetimi programlarıyla kolayca etkileşim kurabilir; Visual Studio kaynak denetimi işlevselliğinin ne kadar çok büyük bir şekilde gerçekleştirildiğine göre, yalnızca kaynak denetimi eklentisi API 'sine göre gerçekleştirilir.

- Kaynak denetimi eklentisi bir kaynak denetimi VSPackage 'tan daha kolay bir şekilde uygulanır.

## <a name="source-control-vspackage"></a>Kaynak denetimi VSPackage
 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] kaynak denetim işlevlerinin tam denetimi ile Visual Studio 'ya derin tümleştirme sağlar ve Visual Studio tarafından sunulan kaynak denetimi kullanıcı arabiriminin yerini alır. Kaynak denetimi VSPackage, Visual Studio ile kaydedilir ve kaynak denetimi işlevselliği sağlar. Birçok kaynak denetimi VSPackages, Visual Studio ile kaydedilebilse de, her bir anda yalnızca biri etkin olabilir. Kaynak denetimi VSPackage, etkin durumdayken Visual Studio 'daki kaynak denetimi işlevselliği ve görünümü üzerinde tam denetime sahiptir. Sistemde kayıtlı olabilecek tüm diğer kaynak denetimi VSPackages 'ları etkin değil ve hiçbir Kullanıcı arabirimini göstermeyecektir.

 Kaynak denetimi VSPackage uygulamak, "tümü veya Nothing" stratejisi gerektirir. Kaynak denetimi VSPackage Oluşturucusu, kaynak denetimi işlevselliğinin tamamını kapsayan bir dizi kaynak denetim arabirimini ve yeni UI öğelerini (iletişim kutuları, menüler ve araç çubukları) uygularken önemli miktarda çaba yatırmalıdır. Daha fazla ayrıntı için bkz. [kaynak denetimi VSPackage oluşturma](../../extensibility/internals/creating-a-source-control-vspackage.md) .

### <a name="drawbacks-to-implementing-a-source-control-vspackage"></a>Kaynak denetimi VSPackage uygulama dezavantajları

- VSPackage, Visual Studio ile başarıyla tümleştirilecek sayıda karmaşık arabirim uygulamalıdır.

- VSPackage, kaynak denetimi için gereken tüm Kullanıcı arabirimini sağlamalıdır; Visual Studio, bu alanda Yardım sağlamaz.

- Kaynak denetimi VSPackage, Visual Studio 'ya bağlı içkin ve tek başına programlarla çalışamaz, bu nedenle işlevler kaynak denetim programının bir dış sürümüyle kolayca paylaşılabilir.

### <a name="advantages-to-implementing-a-source-control-vspackage"></a>Kaynak denetimi VSPackage uygulama avantajları

- VSPackage, kaynak denetimi kullanıcı arabirimi ve işlevselliği üzerinde tam denetime sahip olduğundan, kullanıcıya kaynak denetimi için sorunsuz bir arabirim sunulur.

- VSPackage belirli bir kaynak denetim modeliyle sınırlandırmıyor.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi](../../extensibility/internals/source-control.md)
- [Kaynak Denetimi Eklentisi Oluşturma](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [Kaynak Denetimi VSPackage’ı Oluşturma](../../extensibility/internals/creating-a-source-control-vspackage.md)
- [Kaynak Denetimindeki Yenilikler](../../extensibility/internals/what-s-new-in-source-control.md)
