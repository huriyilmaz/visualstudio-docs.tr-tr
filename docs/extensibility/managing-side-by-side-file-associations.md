---
title: Yan yana dosya Ilişkilendirmelerini yönetme | Microsoft Docs
description: vspackage, dosya ilişkilendirmeleri sağlıyorsa, belirli bir Visual Studio sürümünün bir dosyayı açtığı yan yana yüklemelerin nasıl işleneceğini belirleyin.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126724965"
---
# <a name="manage-side-by-side-file-associations"></a>Yan yana dosya ilişkilendirmelerini yönetme

VSPackage, dosya ilişkilendirmeleri sağlıyorsa, bir dosyayı açmak için belirli bir sürümünün çağrılması gereken yan yana yüklemelerin nasıl işleneceğini seçmelisiniz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Sorunu biçimlendiren uyumsuz dosya biçimleri.

Kullanıcılar bir ürünün yeni bir sürümünü önceki sürümlerle uyumlu olmasını bekler, böylece mevcut dosyalar verileri kaybetmeden yeni bir sürüme yüklenebilir. İdeal olarak, VSPackage, önceki sürümlerin dosya biçimlerini yükleyebilir ve kaydedebilir. Bu doğru değilse, dosya biçimini VSPackage 'ın yeni sürümüne yükseltmeniz gerekir. Bu yaklaşımın dezavantajı, yükseltilen dosyanın önceki sürümde açılamıdır.

Bu sorundan kaçınmak için, dosya biçimleri uyumsuz hale geldiğinde uzantıları değiştirebilirsiniz. Örneğin, VSPackage 'ın 1. sürümü, *. mypkg10* uzantısını kullanabilir ve sürüm 2 ' yi kullanabilir. *mypkg20*. Bu fark, belirli bir dosyayı açan VSPackage 'ı tanımlar. Eski bir uzantıyla ilişkili programlar listesine daha yeni VSPackages eklerseniz, kullanıcılar dosyaya sağ tıklayıp daha yeni bir VSPackage içinde açmayı seçebilir. Bu noktada, VSPackage, dosyayı yeni biçime yükseltebilir veya dosyayı açıp VSPackage 'ın önceki sürümleriyle uyumluluğu sürdürmenize olanak sağlayabilir.

> [!NOTE]
> Bu yaklaşımları birleştirebilirsiniz. Örneğin, daha eski bir dosyayı yükleyerek ve Kullanıcı dosyayı kaydettiğinde dosya biçimini yükseltmek için bir geri uyumluluk sunabilirsiniz.

## <a name="face-the-problem"></a>Sorunun yüzü

Birden çok yan yana VSPackages 'ın aynı uzantıyı kullanmasını istiyorsanız, uzantısıyla ilişkili sürümünü seçmeniz gerekir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Burada iki seçenek vardır:

- Dosyayı bir kullanıcının bilgisayarında yüklü olan en son sürümünde açın [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

   Bu yaklaşımda, yükleyicinizin en son sürümünü belirlemekten [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ve dosya ilişkilendirmesi için yazılan kayıt defteri girişinde de dahil olmak üzere bir sürümü sorumludur. Windows Installer bir pakette, en son sürümünü gösteren bir özelliği ayarlamak için özel eylemler ekleyebilirsiniz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

  > [!NOTE]
  > Bu bağlamda "en son", "en son desteklenen sürüm" anlamına gelir. Bu yükleyici girdileri, sonraki bir sürümünü otomatik olarak algılamaz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . [Yükleme Işleminden sonra çalıştırılması](../extensibility/internals/commands-that-must-be-run-after-installation.md) gereken [sistem gereksinimlerini](../extensibility/internals/detecting-system-requirements.md) ve komutlarını algılayan girişler burada sunulanlara benzerdir ve ek sürümlerini desteklemek için gereklidir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

   CustomAction tablosundaki aşağıdaki satırlar DEVENV_EXE_LATEST özelliğini, [yüklemeden sonra çalıştırılması gereken komutlarda](../extensibility/internals/commands-that-must-be-run-after-installation.md)açıklanan AppSearch ve RegLocator tabloları tarafından ayarlanmış bir özellik olacak şekilde ayarlar. InstallExecuteSequence tablosundaki satırlar özel eylemleri yürütme sırasında erkenden zamanlayın. Koşul sütunundaki değerler, mantık işini yapar:

  - Visual Studio .net 2002, en son sürüm olan tek sürümdür.

  - Visual Studio .net 2003, yalnızca varsa ve mevcut değilse en son sürümdür [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

  - [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] en son sürüm olan tek sürümdür.

    Net sonucu DEVENV_EXE_LATEST en son devenv.exe sürümünün yolunu içerir.

  **Visual Studio en son sürümünü belirten CustomAction tablo satırları**

  |Eylem|Tür|Kaynak|Hedef|
  |------------|----------|------------|------------|
  |CA_SetDevenvLatest_2002|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2002]|
  |CA_SetDevenvLatest_2003|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2003]|
  |CA_SetDevenvLatest_2005|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2005]|

  **Visual Studio en son sürümünü belirten InstallExecuteSequence tablo satırları**

  |Eylem|Koşul|Sequence|
  |------------|---------------|--------------|
  |CA_SetDevenvLatest_2002|DEVENV_EXE_2002 VE NOT (DEVENV_EXE_2003 VEYA DEVENV_EXE_2005)|410|
  |CA_SetDevenvLatest_2003|DEVENV_EXE_2003 DEVENV_EXE_2005 DEĞIL|420|
  |CA_SetDevenvLatest_2005|DEVENV_EXE_2005|430|

   Windows Installer paketinin kayıt defteri tablosundaki DEVENV_EXE_LATEST özelliğini kullanarak **HKEY_CLASSES_ROOT *progıd* shellopencommand** anahtarının varsayılan değerini yazın, [DEVENV_EXE_LATEST] "%1"

- Kullanılabilir VSPackage sürümlerinden en iyi seçimi yapasağlayan bir paylaşılan Başlatıcı programı çalıştırın.

   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]' Nin birçok sürümünden kaynaklanan birden çok çözüm ve proje biçiminin karmaşık gereksinimlerini işlemek için bu yaklaşımı seçtiği geliştiriciler [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Bu yaklaşımda, bir başlatıcı programını uzantı işleyicisi olarak kaydedersiniz. Başlatıcısı dosyayı inceler ve hangi sürümü [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ve VSPackage 'un bu belirli dosyayı işleyebileceğini belirler. Örneğin, bir Kullanıcı VSPackage 'ın belirli bir sürümü tarafından en son kaydedilen bir dosyayı açarsa, Başlatıcı bu VSPackage 'ı eşleşen sürümünde başlatabilir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Ayrıca, bir Kullanıcı, her zaman en son sürümü başlatacak şekilde başlatıcısı yapılandırabilir. Bir başlatıcı ayrıca kullanıcıdan dosyanın biçimini yükseltmesini isteyebilir. Dosyanın biçimi bir sürüm numarası içeriyorsa, dosya biçimi yüklü VSPackages 'lerden daha sonra olan bir sürümden ise Başlatıcı kullanıcıyı bilgilendirir.

   başlatıcı, vspackage 'un tüm sürümleriyle paylaşılan bir Windows Installer bileşende olmalıdır. Bu işlem, en son sürümün her zaman yüklü olduğundan ve VSPackage 'ın tüm sürümleri kaldırılana kadar kaldırılmadığından emin olmanızı sağlar. Bu şekilde, VSPackage 'un bir sürümü kaldırıldıktan sonra bile, başlatıcı bileşeninin dosya ilişkilendirmeleri ve diğer kayıt defteri girdileri korunur.

## <a name="uninstall-and-file-associations"></a>Ve dosya ilişkilendirmelerini kaldır

Dosya ilişkilendirmeleri için kayıt defteri girdilerini yazan VSPackage kaldırıldığında dosya ilişkilendirmeleri kaldırılır. Bu nedenle, uzantının ilişkili programları yok. Windows Yükleyici, VSPackage yüklendiğinde eklenen kayıt defteri girişlerini "kurtarmaz". Bir kullanıcının dosya ilişkilendirmelerini gidermenin bazı yolları aşağıda verilmiştir:

- Daha önce açıklandığı gibi paylaşılan bir başlatıcı bileşeni kullanın.

- Kullanıcıdan, kullanıcının dosya ilişkisine sahip olmasını istediği VSPackage sürümünün onarımını çalıştırmasını isteyin.

- Uygun kayıt defteri girdilerini yeniden oluşturan ayrı bir yürütülebilir program belirtin.

- Kullanıcıların dosya ilişkilendirmelerini seçmesini ve kayıp ilişkilendirmelerini geri kazanmasına imkan tanıyan bir yapılandırma seçenekleri sayfası veya iletişim kutusu sağlayın. Kaldırma işleminden sonra kullanıcılara çalıştırmayı bildirin.

## <a name="see-also"></a>Ayrıca bkz.

- [Yan yana dağıtımlar için dosya adı uzantılarını kaydetme](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)
- [Dosya adı uzantıları için fiilleri kaydetme](../extensibility/registering-verbs-for-file-name-extensions.md)
