---
title: VSPackage Kayıt | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: ecd20da8-b04b-4141-a8f4-a2ef91dd597a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a05dec8fbef40143f31f2c0ac484824717ea2e32
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703927"
---
# <a name="vspackage-registration"></a>VSPackage Kaydı
VSPackages yüklü [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ve yüklenmesi gerektiğini tavsiye etmelidir. Bu işlem, kayıt defterine bilgi yazılarak gerçekleştirilir. Bu, bir yükleyicinin tipik bir işidir.

> [!NOTE]
> VsPackage geliştirme sırasında kendi kendine kayıt kullanmak için kabul edilen bir uygulamadır. Ancak, [!INCLUDE[vsipprvsip](../../extensibility/includes/vsipprvsip_md.md)] ortaklar kurulum un bir parçası olarak kendi kendine kayıt kullanarak ürünlerini sevk edemez.

 Windows Installer paketindeki kayıt defteri girişleri genellikle Kayıt Defteri tablosunda yapılır. Dosya uzantılarını Kayıt Defteri tablosuna da kaydedebilirsiniz. Ancak, Windows Installer programlı tanımlayıcı (ProgId), sınıf, uzantı ve fiil tabloları aracılığıyla yerleşik destek sağlar. Daha fazla bilgi için [Veritabanı Tabloları'na](/windows/desktop/Msi/database-tables)bakın.

 Kayıt defteri girişlerinizin seçtiğiniz yan yana stratejinize uygun bileşenle ilişkili olduğundan emin olun. Örneğin, paylaşılan bir dosyanın kayıt defteri girişleri bu dosyanın Windows Yükleyici bileşeniyle ilişkilendirilmelidir. Benzer şekilde, sürüme özgü bir dosyaiçin kayıt defteri girişleri de bu dosyanın bileşeniyle ilişkilendirilmelidir. Aksi takdirde, VSPackage'ınızı bir sürümü [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] için yüklemek veya kaldırmanız VSPackage'ınızı diğer sürümlerde bozabilir. Daha fazla bilgi için Visual [Studio'nun Birden Çok Sürümlerini Destekleme](../../extensibility/supporting-multiple-versions-of-visual-studio.md)bölümüne bakın.

> [!NOTE]
> Kaydı yönetmenin en kolay yolu, aynı verileri hem geliştirici kaydı hem de yükleme zamanı kaydı için aynı dosyalarda kullanmaktır. Örneğin, bazı yükleyici geliştirme araçları, dosyayı .reg biçiminde, yapı zamanında tüketebilir. Geliştiriciler .reg dosyalarını kendi günlük geliştirme ve hata ayıklamaları için korursa, aynı dosyalar otomatik olarak yükleyiciye eklenebilir. Kayıt verilerini otomatik olarak paylaşamıyorsanız, yükleyicinin kayıt verilerinin kopyasının güncel olduğundan emin olmalısınız.

## <a name="registering-unmanaged-vspackages"></a>Yönetilmeyen VSPackages'ı Kaydetme
 Yönetilmeyen VSPackages (Visual Studio Package Template tarafından oluşturulanlar dahil) kayıt bilgilerini depolamak için ATL tarzı .rgs dosyalarını kullanır. .rgs dosya biçimi ATL'ye özgüdür ve genellikle bir yükleme yazma aracı tarafından olduğu gibi tüketilemez. VSPackage yükleyicisinin kayıt bilgileri ayrıca muhafaza edilmelidir. Örneğin, geliştiriciler dosyaları .rgs dosya değişiklikleriyle eşitleme biçiminde tutabilir. .reg dosyaları geliştirme çalışmaları için RegEdit ile birleştirilebilir veya bir yükleyici tarafından tüketilebilir.

## <a name="registering-managed-vspackages"></a>Yönetilen VSPackages'ı Kaydetme
 RegPkg aracı, yönetilen bir VSPackage'daki kayıt özniteliklerini okur ve bilgileri doğrudan kayıt defterine yazabilir veya yükleyici tarafından tüketilebilen .reg formatLı dosyalar yazabilir.

> [!NOTE]
> RegPkg aracı yeniden dağıtılamaz ve bir VSPackage'ı kullanıcının sistemine kaydetmek için kullanılamaz.

## <a name="why-vspackages-should-not-self-register-at-install-time"></a>VSPackages Yükleme Zamanında Neden Kendi Kendine Kaydolmamalıdır?
 VSPackage yükleyicileriniz kendi kendine kayıt işlemlerine güvenmemelidir. İlk bakışta, bir VSPackage'ın kayıt defteri değerlerini yalnızca VSPackage'ın kendisinde tutmak iyi bir fikir gibi görünüyor. Geliştiricilerin rutin çalışmaları ve testleri için kullanılabilir kayıt defteri değerlerine ihtiyaç duydukları göz önüne alındığında, yükleyicide kayıt defteri verilerinin ayrı bir kopyasını korumaktan kaçınmak mantıklıdır. Yükleyici, kayıt defteri değerlerini yazmak için VSPackage'ın kendisine güvenebilir.

 Teoride iyi olsa da, kendi kendine kayıt VSPackage yükleme için uygun olmayan çeşitli kusurları vardır:

- Yükleme, yükleme yi, yükleme geri alma ve kaldırma geri alma işlemlerini doğru şekilde destekleyen, RegPkg'ı arayarak kendi kendine kaydeden her yönetilen VSPackage için dört özel eylem yazmanızı gerektirir.

- Yan yana desteğe yaklaşımınız, desteklenen her sürümü için RegSvr32 veya RegPkg'ı çağıran [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]dört özel eylem yazmanızı gerektirebilir.

- Kendi kendine kaydedilmiş modüllere sahip bir yükleme güvenli bir şekilde geri alınamaz, çünkü kendi kendine kaydedilmiş anahtarların başka bir özellik veya uygulama tarafından kullanIlip kullanılmadığını söylemenin bir yolu yoktur.

- Kendi kendine kayıtlı DL'ler bazen mevcut olmayan veya yanlış sürüm olan yardımcı DL'lere bağlanır. Buna karşılık, Windows Installer sistemin geçerli durumuna hiçbir bağımlılık ile kayıt defteri tabloları kullanarak DLs kaydedebilirsiniz.

- Bir bileşenin her ikisi de kaynaktan çalıştırolarak belirtilmiş ve SelfReg tablosunda listelenmişse, kendi kendine kayıt kodu tür kitaplıkları gibi ağ kaynaklarına erişimi engellenebilir. Bu, bileşenin yüklenmesinin bir yönetim yüklemesırasında başarısız lığa neden olabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Windows Installer](/windows/desktop/Msi/windows-installer-portal)
- [Yönetilen Paket Kaydı](https://msdn.microsoft.com/library/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)
