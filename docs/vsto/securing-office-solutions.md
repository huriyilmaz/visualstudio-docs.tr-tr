---
title: Office çözümleri güvenli hale getirme
description: Office çözümleri için güvenlik modelinin Office için Visual Studio Araçları çalışma zamanı ve ClickOnce dahil olmak üzere birkaç teknolojiyi nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, security
- Office applications [Office development in Visual Studio], security
- security [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: abe2d548fc79788c650debde06fa1a6847026839
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633806"
---
# <a name="secure-office-solutions"></a>Office çözümleri güvenli hale getirme
  Office çözümleri için güvenlik modeli, çeşitli teknolojiler içerir:, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] Microsoft Office güven merkezi ve ınternet Explorer kısıtlı siteler bölgesi. Aşağıdaki bölümlerde farklı güvenlik özelliklerinin nasıl çalıştığı açıklanır:

- [Office çözümlerine güven verme](#GrantingTrustToSolutions)

- [Belgelere güven verme](#GrantingTrustToDocuments)

- [Windows Installer kullanırken güven verme](#GrantingTrustWindowsInstaller)

- [Office çözümleri için belirli güvenlik konuları](#Security)

- [Geliştirme sırasında güvenlik](#SecurityDuringDeployment)

- [Office çalışma zamanı için Visual Studio Araçları](#VisualStudioToolsForOfficeRuntime)

  [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="grant-trust-to-office-solutions"></a><a name="GrantingTrustToSolutions"></a>Office çözümlerine güven verme
 Office çözümlere güven verilmesi, her bir son kullanıcının güvenlik ilkesini aşağıdaki kanıta göre Office çözümüne güvenmek üzere değiştirme anlamına gelir:

- Dağıtım bildirimini imzalamak için kullanılan sertifika.

- Dağıtım bildiriminin URL 'SI.

  daha fazla bilgi için bkz. [Office çözümlere güven verme](../vsto/granting-trust-to-office-solutions.md).

## <a name="grant-trust-to-documents"></a><a name="GrantingTrustToDocuments"></a> Belgelere güven verme
 Belge düzeyi özelleştirmesi, belgenin güvenilir bir konum olarak belirlenmiş bir dizinde olmasını gerektirir. Daha fazla bilgi için bkz. [belgelere güven verme](../vsto/granting-trust-to-documents.md).

## <a name="grant-trust-when-using-windows-installer"></a><a name="GrantingTrustWindowsInstaller"></a>Windows Installer kullanırken güven verme
 Office çözümlerini, yönetici hakları gerektiren Program dosyaları dizinine yüklemek üzere bir msı dosyası oluşturmak için Windows Installer kullanabilirsiniz. Program dosyaları dizinindeki Office çözümleri için, Office çalışma zamanına yönelik Visual Studio 2010 araçları bu Office çözümlerini güvenilir olarak değerlendirir ve ClickOnce güven istemi 'ni göstermez.

## <a name="specific-security-considerations-for-office-solutions"></a><a name="Security"></a>Office çözümleri için belirli güvenlik konuları
 , ve Microsoft Office tarafından sağlanan güvenlik özellikleri [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] Office çözümlerinde çeşitli olası güvenlik tehditlerine karşı korumaya yardımcı olabilir. daha fazla bilgi için bkz. [Office çözümlere yönelik belirli güvenlik konuları](../vsto/specific-security-considerations-for-office-solutions.md).

## <a name="security-during-development"></a><a name="SecurityDuringDeployment"></a> Geliştirme sırasında güvenlik
 geliştirme sürecinizi daha kolay hale getirmek için Visual Studio, bir projeyi her oluşturduğunuzda çözümünüzde çalıştırmak ve çözümünüzde hata ayıklaması yapmak için gereken güvenlik ilkesini ayarlar. Bazı senaryolarda, projeyi geliştirmek için ek güvenlik adımları uygulamanız gerekebilir.

### <a name="document-level-solutions"></a>Belge düzeyi çözümler
 aşağıdaki proje türlerini geliştiriyorsanız, bir belgenin tam yolu Microsoft Office uygulamasındaki güvenilir konumlar listesine eklenmelidir:

- *\\ \ Sunucuadı \ PaylaşımAdı* gibi bir ağ dosya paylaşımında bulunan belge düzeyi çözümler.

- *.doc* veya *. docm* dosyalarını kullanan Word için belge düzeyi çözümleri.

  Belge konumunu Güvenilen konumlar listesine eklediğinizde veya özel olarak hata ayıklama ve yapı klasörlerini dahil ettiğinizde alt dizinleri ekleyin. daha fazla bilgi için, [dosyalarınız için güvenilir bir konum oluşturma, kaldırma veya değiştirme](https://support.office.com/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62)Microsoft Office çevrimiçi yardım makalesini inceleyin.

### <a name="temporary-certificates"></a>Geçici sertifikalar
 Visual Studio imza sertifikası zaten yoksa geçici bir sertifika oluşturur. Bu geçici sertifikayı yalnızca geliştirme sırasında kullanmanız ve dağıtım için resmi bir sertifika satın almanız gerekir.

 geçici sertifika, bir Office projesi ilk derlendikten sonra oluşturulur. **F5** tuşuna bastığınızda proje yeniden oluşturulur çünkü proje, sertifika eklendiğinde değişiklik olarak işaretlenir.

 Bir süre sonra çok sayıda geçici sertifika olabilir, bu nedenle geçici sertifikaları bazen temizlemeniz gerekir.

## <a name="visual-studio-tools-for-office-runtime"></a><a name="VisualStudioToolsForOfficeRuntime"></a>Office için Visual Studio Araçları çalışma zamanı
 , [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Yayımcının kimliğini ve bir özelleştirmeye verilen izinleri doğrulamak için özelliklere sahiptir. Bu izinleri bir dizi güvenlik denetimi aracılığıyla doğrular.

### <a name="security-during-customization-loading"></a>Özelleştirme yükleme sırasında güvenlik
 Belge düzeyi özelleştirmesi yüklendiğinde, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] her zaman belgenin güvenilir konumlar listesinde olup olmadığını denetler. Ayrıca, çalışma zamanı çözümün uygulama bildiriminde FullTrust isteyip istemediğini denetler. Özelleştirme yüklenirken ek bir güvenlik denetimi yapılmaz.

### <a name="sequence-of-security-checks-during-installation"></a>Yükleme sırasında güvenlik denetimlerinin sırası
 bir Office çözümü yüklendiğinde veya güncelleştirilirken, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] güven kararı vermek için belirli bir sırada bir dizi güvenlik denetimi gerçekleştirir. Bir çözüm, yalnızca çalışma zamanı çözümün güvenilir olduğunu belirlerse yüklenir veya güncelleştirilir.

 yükleme işlemini dört şekilde başlatabilirsiniz: kurulum programını çalıştırarak, Microsoft Office uygulama konağını açarak veya *VSTOInstaller.exe* çalıştırarak dağıtım bildirimini açarak.

 İlk güvenlik denetimi yalnızca belge düzeyi çözümler için geçerlidir. Belge düzeyi çözümünün belgesi, güvenilir bir konumda olmalıdır. Belge, uzak bir ağ dosya paylaşımındaysa veya *.doc* veya *. docm* dosya adı uzantısına sahipse, belgenin konumu güvenilen konumlar listesine eklenmelidir. Daha fazla bilgi için bkz. [belgelere güven verme](../vsto/granting-trust-to-documents.md).

 ![Microsoft Office VSTO güvenliği-yükleme](../vsto/media/host-install.png "Microsoft Office VSTO güvenliği-yükleme")

 Sonraki güvenlik denetimleri kümesi, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ve ClickOnce. bu denetimleri geçirmek için Office çözümlerin FullTrust izinleri istemesi, güvenilmeyen Publisher listesinde listelenmeyen bir sertifikayla imzalanması ve ınternet Explorer kısıtlı bölgesinde olmayan bir konumda olması gerekir. sertifika, güvenilir Publisher listesinde yer alıyorsa çözüm hemen yüklenir. Aksi takdirde, denetimlerden biri başarısız olduysa, çözüm son denetim kümesine devam eder.

 ![çözümleri yüklemek için VSTO güvenliği](../vsto/media/installing.png "çözümleri yüklemek için VSTO güvenliği")

 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]Güven istemi 'ne izin veriliyorsa ve çözüme henüz güven verilmemişse, çalışma zamanı Son Kullanıcı tarafından güven kararının yapılmasına izin verir. Kullanıcı çözüme güven veriyorsa, Kullanıcı ekleme listesine bir giriş eklenir. Kullanıcı ekleme listesindeki tüm çözümler tam güvene sahiptir ve yüklenebilir ve çalıştırılabilir.

 Visual Studio 2010 ' den başlayarak, Office çözümü Program dosyaları dizinine Windows Installer (msı) kullanılarak yüklenirse ekleme listesi atlanır. daha fazla bilgi için bkz. [ekleme listeleri kullanarak güvenilir Office çözümleri](../vsto/trusting-office-solutions-by-using-inclusion-lists.md).

 ![VSTO güvenliği-yüklemek için kurulum programını kullanma](../vsto/media/setup-vstoinstaller.png "VSTO güvenliği-yüklemek için kurulum programını kullanma")

## <a name="see-also"></a>Ayrıca bkz.

- [Office çözümlerine güven verme](../vsto/granting-trust-to-office-solutions.md)
- [Belgelere güven verme](../vsto/granting-trust-to-documents.md)
- [ekleme listelerini kullanarak Office çözümlere güven](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)
- [Nasıl yapılır: ekleme listesi güvenliğini yapılandırma](../vsto/how-to-configure-inclusion-list-security.md)
- [nasıl yapılır: Office çözümlerini imzalama](../vsto/how-to-sign-office-solutions.md)
- [Office çözüm güvenliği sorunlarını giderme](../vsto/troubleshooting-office-solution-security.md)
- [Office çözümleri için uygulama bildirimleri](../vsto/application-manifests-for-office-solutions.md)
- [Office çözümleri için dağıtım bildirimleri](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce başvurusu](../deployment/clickonce-reference.md)
- [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)
