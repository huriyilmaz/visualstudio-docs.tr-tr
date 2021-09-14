---
title: VSPackage Kayıt | Microsoft Docs
description: Paketlerin yüklü olduğunu ve kayıt defterine bilgi yazarak Visual Studio gerektiğini önerip yüklemeleri gerektiği VSPackage kaydı hakkında bilgi alın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: ecd20da8-b04b-4141-a8f4-a2ef91dd597a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: f0257eb175dff65a28cc942ef4854cfdff437d5c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126724996"
---
# <a name="vspackage-registration"></a>VSPackage Kaydı
VSPackage'lar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] yüklendiklerini ve yüklenmeleri gerektiğini öneriltir. Bu işlem kayıt defterine bilgi yazarak başarılı olur. Bu, bir yükleyicinin tipik bir işidir.

> [!NOTE]
> Kendi kendine kayıt kullanmak VSPackage geliştirme sırasında kabul edilen bir uygulamadır. Ancak, [!INCLUDE[vsipprvsip](../../extensibility/includes/vsipprvsip_md.md)] iş ortakları kurulumun bir parçası olarak kendi kendine kayıt kullanarak ürünlerini gönderamaz.

 Windows Installer paketinde kayıt defteri girişleri genellikle Kayıt Defteri tablosunda yapılır. Dosya uzantılarını Kayıt Defteri tablosuna da kaydedebilirsiniz. Ancak Windows Yükleyicisi program tanımlayıcısı (ProgId), sınıf, uzantı ve fiil tabloları aracılığıyla yerleşik destek sağlar. Daha fazla bilgi için [bkz. Veritabanı Tabloları.](/windows/desktop/Msi/database-tables)

 Kayıt defteri girdilerinin seçtiğiniz yan yana stratejinize uygun bileşenle ilişkilendiril olduğundan emin olun. Örneğin, paylaşılan bir dosyanın kayıt defteri girdileri, bu dosyanın Windows yükleyici bileşeniyle ilişkilendirilmiş olması gerekir. Benzer şekilde, sürüme özgü bir dosyanın kayıt defteri girdileri bu dosyanın bileşeniyle ilişkili olması gerekir. Aksi takdirde, bir sürümü için VSPackage'nızı yüklemek veya kaldırmak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage'nızı diğer sürümlerde bozabilirsiniz. Daha fazla bilgi için, [bkz. Supporting Multiple Versions of Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md).

> [!NOTE]
> Kaydı yönetmenin en kolay yolu, aynı verileri hem geliştirici kaydı hem de yükleme zamanı kaydı için aynı dosyalarda kullanmaktır. Örneğin, bazı yükleyici geliştirme araçları derleme zamanında dosyayı .reg biçiminde tüketir. Geliştiriciler günlük geliştirme ve hata ayıklama için .reg dosyalarını bulundurıyorsa, aynı dosyalar yükleyiciye otomatik olarak dahil olabilir. Kayıt verilerini otomatik olarak paylaşamazsanız, yükleyicinin kayıt verileri kopyasının güncel olduğundan emin olmak gerekir.

## <a name="registering-unmanaged-vspackages"></a>Unmanaged VSPackages Kaydetme
 Unmanaged VSPackages (Visual Studio Paket Şablonu tarafından oluşturulanlar dahil) kayıt bilgilerini depolamak için ATL stili .rgs dosyalarını kullanır. .rgs dosya biçimi ATL'ye özeldir ve genellikle bir yükleme yazma aracı tarafından olduğu gibi kullanılamaz. VSPackage yükleyicisi için kayıt bilgileri ayrı ayrı tutulmalıdır. Örneğin, geliştiriciler dosyaları .rgs dosya değişiklikleriyle eşitlenen .reg biçiminde tutabilirsiniz. Geliştirme işi için .reg dosyaları RegEdit ile birleştirilebilir veya bir yükleyici tarafından kullanılabilir.

## <a name="registering-managed-vspackages"></a>Yönetilen VSPackage'ları Kaydetme
 RegPkg aracı, yönetilen bir VSPackage'dan kayıt özniteliklerini okur ve bilgileri doğrudan kayıt defterine yazabilir veya bir yükleyici tarafından tüketilen .reg biçimindeki dosyaları yazabilir.

> [!NOTE]
> RegPkg aracı yeniden dağıtılamaz ve kullanıcının sistemine VSPackage kaydetmek için kullanılamaz.

## <a name="why-vspackages-should-not-self-register-at-install-time"></a>VSPackages Yükleme Zamanında Self-Register Neden Yüklenmeli?
 VSPackage yükleyicileri kendi kendine kayıt işlemini kullanmaz. İlk bakışta, vsPackage'ın kayıt defteri değerlerini yalnızca VSPackage'ın içinde tutmak iyi bir fikir gibi görünebilir. Geliştiricilerin rutin çalışmaları ve testleri için kullanılabilir kayıt defteri değerlerine ihtiyacı olduğu için, kayıt defteri verilerini yükleyicide ayrı bir kopyasının korunmasından kaçınmak mantıklıdır. Yükleyici, kayıt defteri değerlerini yazmak için VSPackage'ın kendisine güvenebilirsiniz.

 Teoride iyi bir şey de, kendi kendine kayıt işleminin VSPackage yüklemesi için uygun olmayan bazı açıkları vardır:

- Yüklemeyi, kaldırmayı, yükleme geri alma ve kaldırma geri alma işlemini doğru desteklemek için RegPkg'yi çağırarak kendi kendine kaydolan her yönetilen VSPackage için dört özel eylem yazmanız gerekir.

- Yan yana destek yaklaşımınız, desteklenen her sürümü için RegSvr32 veya RegPkg'yi çağıran dört özel eylem yazmanızı [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gerektirir.

- Kendi kendine kayıtlı modülleri olan bir yükleme güvenli bir şekilde geri alınamaz çünkü kendi kendine kaydedilen anahtarların başka bir özellik veya uygulama tarafından kullanılıp kullanılmay olmadığını söylemenin bir yolu yoktur.

- Kendi kendine kaydedilen URL'ler bazen mevcut olmayan veya yanlış sürümde olan yardımcı URL'lere bağlantı sağlar. Buna karşılık, Windows Yükleyici sistemin geçerli durumuna bağımlılıksız olarak kayıt defteri tablolarını kullanarak URL'leri kaydedebilirsiniz.

- Bir bileşenin her ikisi de kaynaktan çalıştır olarak belirtilmişse ve SelfReg tablosunda listelenmişse, tür kitaplıkları gibi ağ kaynaklarına kendi kendine kayıt kodu erişimi reddedilebilir. Bu, bileşenin yüklenmesi bir yönetim yüklemesi sırasında başarısız olabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Windows Installer](/windows/desktop/Msi/windows-installer-portal)
- [Yönetilen Paket Kaydı](/previous-versions/bb166783(v=vs.100))