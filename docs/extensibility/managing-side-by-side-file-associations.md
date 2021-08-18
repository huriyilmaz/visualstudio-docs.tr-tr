---
title: Yan Yana Dosya İlişkilerini Yönetme | Microsoft Docs
description: VSPackage dosya ilişkilendirmeleri sağlarsa, belirli bir dosya sürümünün bir dosyayı açtığı yan yana yüklemelerin Visual Studio karar verin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- verbs, setting default
ms.assetid: 9b6df3bc-d15c-4a5d-9015-948a806193b7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 306643116e295342bcfb602eef370af418c87733
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122152204"
---
# <a name="manage-side-by-side-file-associations"></a>Yan yana dosya ilişkilendirmelerini yönetme

VSPackage dosya ilişkilendirmeleri sağlarsa, bir dosyayı açmak için belirli bir sürümünün çağrılsı gereken yan yana yüklemeleri nasıl işley karar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] verebilirsiniz. Uyumsuz dosya biçimleri sorunu bileşiktir.

Kullanıcılar, bir ürünün yeni sürümünün önceki sürümlerle uyumlu olmasını bekler, böylece mevcut dosyalar veri kaybetmeden yeni bir sürüme yüklenebilir. İdeal olarak, VSPackage'nız hem yük hem de önceki sürümlerin dosya biçimlerini kaydedebilir. Bu doğru değildir, dosya biçimini VSPackage'nizin yeni sürümüne yükseltmeyi sunabilirsiniz. Bu yaklaşımın dezavantajı, yükseltilen dosyanın önceki sürümde açılamay olmasıdır.

Bu sorunu önlemek için, dosya biçimleri uyumsuz hale geldiğinde uzantıları değiştirebilirsiniz. Örneğin VSPackage sürüm *1.mypkg10* uzantısını, sürüm 2 de *.mypkg20 uzantısını kullanabilir.* Bu fark, belirli bir dosyayı açan VSPackage'i tanımlar. Eski bir uzantıyla ilişkili programlar listesine daha yeni VSPackage'lar eklersiniz, kullanıcılar dosyaya sağ tıklar ve dosyayı daha yeni bir VSPackage'da açmayı seçebilir. Bu noktada VSPackage'nız dosyayı yeni biçime yükseltmeyi veya dosyayı açmayı ve VSPackage'ın önceki sürümleriyle uyumluluğu korumayı teklif ediyor olabilir.

> [!NOTE]
> Bu yaklaşımları birleştirin. Örneğin, eski bir dosyayı yükerek geriye dönük uyumluluk silebilir ve kullanıcı dosyayı kaydederken dosya biçimini yükseltmeyi teklif edebilir.

## <a name="face-the-problem"></a>Sorunla Karşılaş

Birden çok yan yana VSPackage'ın aynı uzantıyı kullanması için uzantıyla [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ilişkili sürümünü seçmeniz gerekir. İki alternatif vardır:

- Dosyayı kullanıcının bilgisayarına yüklenmiş [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] olan en son sürümünde açın.

   Bu yaklaşımda yükleyiciniz, dosya ilişkilendirmesi için yazılan kayıt defteri girdisine dahil olmak üzere en son [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sürümünü belirlemekle sorumludur. Bir Windows Yükleyici paketinde, en son sürümünü belirten bir özellik ayarlamak için özel eylemler dahil [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] edin.

  > [!NOTE]
  > Bu bağlamda "latest" (en son sürüm) "desteklenen en son sürüm" anlamına gelir. Bu yükleyici girişleri sonraki bir sürümü otomatik olarak [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] algılamaz. Sistem Gereksinimlerini [Algılama ve](../extensibility/internals/detecting-system-requirements.md) [](../extensibility/internals/commands-that-must-be-run-after-installation.md) YüklemeDen Sonra Çalıştıracak Komutlar'daki girdiler burada sunulanlara benzer ve ek sürümlerini desteklemek için [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] gereklidir.

   CustomAction tablosunda yer alan aşağıdaki satırlar, DEVENV_EXE_LATEST özelliğini, yüklemeden sonra çalıştırılacak Komutlar'da ele alınan AppSearch ve RegLocator tabloları tarafından ayarlanmış bir [özellik olarak ayarlamıştır.](../extensibility/internals/commands-that-must-be-run-after-installation.md) InstallExecuteSequence tablosunda yer alan satırlar, yürütme sırasının başlarında özel eylemleri zamanlar. Koşul sütunundaki değerler mantığın çalışmasına neden olur:

  - Visual Studio .NET 2002, mevcut tek sürüm ise en son sürümdür.

  - Visual Studio .NET 2003 yalnızca varsa ve mevcutsa en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] son sürümdür.

  - [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , mevcut tek sürüm ise en son sürümdür.

    Sonuç olarak DEVENV_EXE_LATEST en son sürümünün yolunu devenv.exe.

  **Uygulamanın en son sürümünü belirleyen CustomAction tablo Visual Studio**

  |Eylem|Tür|Kaynak|Hedef|
  |------------|----------|------------|------------|
  |CA_SetDevenvLatest_2002|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2002]|
  |CA_SetDevenvLatest_2003|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2003]|
  |CA_SetDevenvLatest_2005|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2005]|

  **Uygulamanın en son sürümünü belirleyen InstallExecuteSequence tablo Visual Studio**

  |Eylem|Koşul|Sequence|
  |------------|---------------|--------------|
  |CA_SetDevenvLatest_2002|DEVENV_EXE_2002 AND NOT (DEVENV_EXE_2003 OR DEVENV_EXE_2005)|410|
  |CA_SetDevenvLatest_2003|DEVENV_EXE_2003 VE NOT DEVENV_EXE_2005|420|
  |CA_SetDevenvLatest_2005|DEVENV_EXE_2005|430|

   Windows Installer paketinin Registry tablosunda DEVENV_EXE_LATEST özelliğini kullanarak **HKEY_CLASSES_ROOT *ProgId* ShellOpenCommand** anahtarının varsayılan değerini [DEVENV_EXE_LATEST] "%1"

- Kullanılabilir VSPackage sürümlerinden en iyi seçimi seçen bir paylaşılan başlatıcı programı çalıştırın.

   geliştiricileri, birçok sürümüyle elde edilen çözüm ve projelerin birden çok biçimine yönelik karmaşık gereksinimleri [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] işlemek için bu yaklaşımı tercih [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] etti. Bu yaklaşımda, bir başlatıcı programını uzantı işleyicisi olarak kaydedersiniz. Başlatıcı dosyayı inceler ve hangi sürümünün ve [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSPackage'nizin bu dosyayı işleyene karar verir. Örneğin, bir kullanıcı VSPackage'nizin belirli bir sürümü tarafından son kaydedilen bir dosyayı açarsa, başlatıcı bu VSPackage'i eşleşen sürümünde [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] başlatabilirsiniz. Ayrıca, bir kullanıcı her zaman en son sürümü başlatmak için başlatıcıyı yapılandırabilirsiniz. Başlatıcı bir kullanıcıdan dosyanın biçimini yükseltmesi de istendiğinde. Dosyanın biçimi bir sürüm numarası içerirse, başlatıcı dosya biçiminin yüklü VSPackage'lardan bir veya daha fazlası olan bir sürümden mi olduğunu kullanıcıya bildirmiş olabilir.

   Başlatıcı, VSPackage'Windows tüm sürümleriyle paylaşılan bir Yükleyici bileşeninde yer aladır. Bu işlem, en son sürümün her zaman yüklü olduğundan ve VSPackage'nizin tüm sürümleri kaldırılana kadar kaldırılmaz. Bu şekilde, VSPackage'ın bir sürümü kaldırılmış olsa bile başlatıcı bileşeninin dosya ilişkilendirmeleri ve diğer kayıt defteri girişleri korunur.

## <a name="uninstall-and-file-associations"></a>Kaldırma ve dosya ilişkilendirmeleri

Dosya ilişkilendirmeleri için kayıt defteri girdileri yazan bir VSPackage'ın kaldırılması, dosya ilişkilendirmelerini kaldırır. Bu nedenle uzantının ilişkili bir programı yoktur. Windows Yükleyici, VSPackage yüklenirken eklenen kayıt defteri girdilerini "kurtarmaz". Bir kullanıcının dosya ilişkilendirmelerini düzeltmenin bazı yolları:

- Daha önce açıklandığı gibi bir paylaşılan başlatıcı bileşeni kullanın.

- Kullanıcıya VSPackage sürümünün dosya ilişkilendirmeye sahip olmak istediği bir onarımı çalıştırması talimatı.

- Uygun kayıt defteri girdilerini yeniden yazacak ayrı bir yürütülebilir program sağlama.

- Kullanıcıların dosya ilişkilendirmelerini seçmelerini ve kayıp ilişkilendirmeleri geri alamalarını sağlayan bir yapılandırma seçenekleri sayfası veya iletişim kutusu sağlar. Kullanıcılara kaldırma sonrasında çalıştırmalarını talimatı vere.

## <a name="see-also"></a>Ayrıca bkz.

- [Yan yana dağıtımlar için dosya adı uzantılarını kaydetme](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)
- [Dosya adı uzantıları için fiilleri kaydetme](../extensibility/registering-verbs-for-file-name-extensions.md)
