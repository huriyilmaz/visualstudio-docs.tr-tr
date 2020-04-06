---
title: Yan Yana Dosya Çağrışımlarını Yönetme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- verbs, setting default
ms.assetid: 9b6df3bc-d15c-4a5d-9015-948a806193b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6c284fe7ef4c2d07051a8524860583cb634e13bf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702757"
---
# <a name="manage-side-by-side-file-associations"></a>Yan yana dosya ilişkilendirmelerini yönetme

VSPackage dosya ilişkilendirmeleri sağlıyorsa, bir dosyayı açmak için belirli bir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sürümün çağrılması gereken yan yana yüklemeleri nasıl işleyeceğinize karar vermeniz gerekir. Uyumsuz dosya biçimleri sorunu bileşik.

Kullanıcılar, varolan dosyaların veri kaybetmeden yeni bir sürüme yüklenebileceği için ürünün yeni bir sürümünün önceki sürümlerle uyumlu olmasını bekler. İdeal olarak, VSPackage'ınız önceki sürümlerin dosya biçimlerini yükleyebilir ve kaydedebilir. Bu doğru değilse, dosya biçimini VSPackage'ınızın yeni sürümüne yükseltmeyi önermelisiniz. Bu yaklaşımın dezavantajı, yükseltilen dosyanın önceki sürümde açılamamasıdır.

Bu sorunu önlemek için, dosya biçimleri uyumsuz olduğunda uzantıları değiştirebilirsiniz. Örneğin, VSPackage sürüm 1 uzantısı kullanabilirsiniz, *.mypkg10*, ve sürüm 2 uzantısı kullanabilirsiniz, *.mypkg20*. Bu fark, belirli bir dosyayı açan VSPackage'ı tanımlar. Eski bir uzantıyla ilişkili programlar listesine daha yeni VSPackages eklerseniz, kullanıcılar dosyayı sağ tıklayabilir ve dosyayı daha yeni bir VSPackage'da açmayı seçebilir. Bu noktada, VSPackage'ınız dosyayı yeni biçime yükseltmeyi veya dosyayı açmayı ve VSPackage'ın önceki sürümleriyle uyumluluğu korumayı sunabilir.

> [!NOTE]
> Bu yaklaşımları birleştirebilirsiniz. Örneğin, eski bir dosyayükleyerek geriye dönük uyumluluk sunabilir ve kullanıcı kaydettiğinde dosya biçimini yükseltmeyi teklif edebilirsiniz.

## <a name="face-the-problem"></a>Sorunla Yüzleşin

Aynı uzantıyı kullanmak için birden çok yan yana VSPackages istiyorsanız, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bunun uzantısı ile ilişkili sürümünü seçmeniz gerekir. İşte iki alternatif:

- Dosyayı, kullanıcının [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bilgisayarında yüklenen en son sürümde açın.

   Bu yaklaşımda, yükleyiciniz dosya ilişkilendirmesi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] için yazılmış kayıt defteri girişinin en son sürümünü belirlemekten sorumludur. Windows Installer paketinde, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]'nin en son sürümünü gösteren bir özellik ayarlamak için özel eylemler ekleyebilirsiniz

  > [!NOTE]
  > Bu bağlamda, "en son" "en son desteklenen sürüm" anlamına gelir. Bu yükleyici girişleri otomatik olarak bir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]sonraki sürümü algılamaz. Sistem [Gereksinimlerini Algılama](../extensibility/internals/detecting-system-requirements.md) girişleri ve [Kurulumdan Sonra Çalıştırılması Gereken Komutlar,](../extensibility/internals/commands-that-must-be-run-after-installation.md) burada sunulanlara benzer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ve ek sürümlerini desteklemek için gereklidir.

   CustomAction tablosundaki aşağıdaki satırlar, DEVENV_EXE_LATEST [özelliğini, yüklemeden sonra çalıştırılması gereken Komutlarda](../extensibility/internals/commands-that-must-be-run-after-installation.md)tartışılan AppSearch ve RegLocator tabloları tarafından ayarlanan bir özellik olarak ayarlar. InstallExecuteSequence tablosundaki satırlar, özel eylemleri yürütme sırasının başlarında zamanlar. Koşul sütunundaki değerler mantığın çalışmasını sağlar:

  - Visual Studio .NET 2002 mevcut tek sürüm ise en son sürümüdür.

  - Visual Studio .NET 2003 sadece mevcut ve [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] mevcut değilse en son sürümüdür.

  - [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]tek mevcut sürümü ise en son sürümüdür.

    Net sonuç DEVENV_EXE_LATEST devenv.exe en son sürümünün yolunu içerir olmasıdır.

  **Visual Studio'nun en son sürümünü belirleyen CustomAction tablo satırları**

  |Eylem|Tür|Kaynak|Hedef|
  |------------|----------|------------|------------|
  |CA_SetDevenvLatest_2002|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2002]|
  |CA_SetDevenvLatest_2003|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2003]|
  |CA_SetDevenvLatest_2005|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2005]|

  **Visual Studio'nun en son sürümünü belirleyen InstallExecuteSequence tablo satırları**

  |Eylem|Koşul|Sequence|
  |------------|---------------|--------------|
  |CA_SetDevenvLatest_2002|DEVENV_EXE_2002 VE Değİl (DEVENV_EXE_2003 VEYA DEVENV_EXE_2005)|410|
  |CA_SetDevenvLatest_2003|DEVENV_EXE_2003 VE DEVENV_EXE_2005 Değİl|420|
  |CA_SetDevenvLatest_2005|DEVENV_EXE_2005|430|

   Windows Installer paketinin Kayıt Defteri tablosundaki DEVENV_EXE_LATEST özelliğini kullanarak ***ProgId*ShellOpenCommand** tuşu'nun varsayılan değerini HKEY_CLASSES_ROOT yazabilirsiniz, [DEVENV_EXE_LATEST] "%1"

- Mevcut VSPackage sürümlerinden en iyi seçimi yapabilecek paylaşılan bir başlatıcı programı çalıştırın.

   Geliştiriciler, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] birçok sürümünden kaynaklanan çözümler in birden çok çözüm ve proje biçiminin [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]karmaşık gereksinimlerini işlemek için bu yaklaşımı seçti. Bu yaklaşımda, uzantı işleyicisi olarak bir başlatıcı programı kaydedin. Başlatıcı dosyayı inceler ve VSPackage'ınızın hangi sürümünün ve sizin bu dosyayı [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] işleyebileceğine karar verir. Örneğin, bir kullanıcı VSPackage'ınızın belirli bir sürümü tarafından en son kaydedilen bir dosyayı açarsa, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]başlatıcı bu VSPackage'ı eşleşen sürümünde başlatabilir. Buna ek olarak, bir kullanıcı her zaman en son sürümü başlatmak için başlatıcısı yapılandırabilir. Başlatıcı, kullanıcıyı dosyanın biçimini yükseltmeye de itebilir. Dosyanın biçimi bir sürüm numarası içeriyorsa, dosya biçimi yüklenen VSPackages'lerden bir veya daha fazla olan bir sürümden geliyorsa başlatıcı kullanıcıyı bilgilendirebilir.

   Başlatıcı, VSPackage'ınızın tüm sürümleriyle paylaşılan bir Windows Installer bileşeninde olmalıdır. Bu işlem, en son sürümün her zaman yüklendiğinden ve VSPackage'ınızın tüm sürümleri kaldırılana kadar kaldırılmamasını sağlar. Bu şekilde, VSPackage'ın bir sürümü kaldırılsa bile, başlatıcı bileşeninin dosya ilişkilendirmeleri ve diğer kayıt defteri girişleri korunur.

## <a name="uninstall-and-file-associations"></a>Kaldırma ve dosya çağrışımları

Dosya ilişkilendirmeleri için kayıt defteri girişleri yazan bir VSPackage kaldırma dosya ilişkilendirmeleri kaldırır. Bu nedenle, uzantı ilişkili programları vardır. Windows Installer, VSPackage yüklendiğinde eklenen kayıt defteri girişlerini "kurtarmaz". Bir kullanıcının dosya ilişkilendirmelerini düzeltmenin bazı yolları şunlardır:

- Daha önce açıklandığı gibi paylaşılan bir başlatıcı bileşeni kullanın.

- Kullanıcıya, kullanıcının dosya ilişkilendirmesine sahip olmak istediği VSPackage sürümünün onarımını çalıştırmasını talimat edin.

- Uygun kayıt defteri girişlerini yeniden yazan ayrı bir yürütülebilir program sağlayın.

- Kullanıcıların dosya ilişkilendirmelerini seçmesini ve kayıp ilişkileri geri almalarını sağlayan bir yapılandırma seçenekleri sayfası veya iletişim kutusu sağlayın. Kullanıcılara yüklemeyi kaldırmadan sonra çalıştırmalarını talimat edin.

## <a name="see-also"></a>Ayrıca bkz.

- [Yan yana dağıtımlar için dosya adı uzantılarını kaydetme](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)
- [Dosya adı uzantıları için fiilleri kaydetme](../extensibility/registering-verbs-for-file-name-extensions.md)
