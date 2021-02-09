---
title: Güvenli Office çözümleri
description: Office çözümleri için güvenlik modelinin, Office çalışma zamanı ve ClickOnce için Visual Studio Araçları dahil olmak üzere birkaç teknolojiyi nasıl kullandığını öğrenin.
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
ms.workload:
- office
ms.openlocfilehash: 3576bdc41f25b95b68230e09e07b1a5ed97016c6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906658"
---
# <a name="secure-office-solutions"></a>Güvenli Office çözümleri
  Office çözümleri için güvenlik modeli çeşitli teknolojiler içerir:,, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] Microsoft Office Güven Merkezi ve Internet Explorer kısıtlı siteler bölgesi. Aşağıdaki bölümlerde farklı güvenlik özelliklerinin nasıl çalıştığı açıklanır:

- [Office çözümlerine güven verme](#GrantingTrustToSolutions)

- [Belgelere güven verme](#GrantingTrustToDocuments)

- [Windows Installer kullanırken güven verme](#GrantingTrustWindowsInstaller)

- [Office çözümleri için belirli güvenlik konuları](#Security)

- [Geliştirme sırasında güvenlik](#SecurityDuringDeployment)

- [Office çalışma zamanı için Visual Studio Araçları](#VisualStudioToolsForOfficeRuntime)

  [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="grant-trust-to-office-solutions"></a><a name="GrantingTrustToSolutions"></a> Office çözümlerine güven verme
 Office çözümlerine güven verilmesi, her son kullanıcının güvenlik ilkesini aşağıdaki kanıta göre Office çözümüne güvenmek üzere değiştirme anlamına gelir:

- Dağıtım bildirimini imzalamak için kullanılan sertifika.

- Dağıtım bildiriminin URL 'SI.

  Daha fazla bilgi için bkz. [Office çözümlerine güven verme](../vsto/granting-trust-to-office-solutions.md).

## <a name="grant-trust-to-documents"></a><a name="GrantingTrustToDocuments"></a> Belgelere güven verme
 Belge düzeyi özelleştirmesi, belgenin güvenilir bir konum olarak belirlenmiş bir dizinde olmasını gerektirir. Daha fazla bilgi için bkz. [belgelere güven verme](../vsto/granting-trust-to-documents.md).

## <a name="grant-trust-when-using-windows-installer"></a><a name="GrantingTrustWindowsInstaller"></a> Windows Installer kullanırken güven verme
 Office çözümlerini, yönetici hakları gerektiren program dosyaları dizinine yüklemek üzere bir MSI dosyası oluşturmak için Windows Installer kullanabilirsiniz. Program dosyaları dizinindeki Office çözümleri için, Office çalışma zamanı için Visual Studio 2010 araçları, bu Office çözümlerini güvenilir kabul eder ve ClickOnce güven istemi 'ni göstermez.

## <a name="specific-security-considerations-for-office-solutions"></a><a name="Security"></a> Office çözümleri için belirli güvenlik konuları
 , Ve Microsoft Office tarafından sağlanan güvenlik özellikleri, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] Office çözümlerinde çeşitli olası güvenlik tehditlerine karşı korumaya yardımcı olabilir. Daha fazla bilgi için bkz. [Office çözümleri Için belirli güvenlik konuları](../vsto/specific-security-considerations-for-office-solutions.md).

## <a name="security-during-development"></a><a name="SecurityDuringDeployment"></a> Geliştirme sırasında güvenlik
 Geliştirme sürecinizi daha kolay hale getirmek için, Visual Studio, bir projeyi her oluşturduğunuzda çözümünüzde çalıştırmak ve çözümünüzde hata ayıklamak için gereken güvenlik ilkesini ayarlar. Bazı senaryolarda, projeyi geliştirmek için ek güvenlik adımları uygulamanız gerekebilir.

### <a name="document-level-solutions"></a>Belge düzeyi çözümler
 Aşağıdaki proje türlerini geliştiriyorsanız, bir belgenin tam yolu Microsoft Office uygulamasındaki güvenilir konumlar listesine eklenmelidir:

- *\\ \ Sunucuadı \ PaylaşımAdı* gibi bir ağ dosya paylaşımında bulunan belge düzeyi çözümler.

- *. Doc* veya *. docm* dosyalarını kullanan Word için belge düzeyi çözümleri.

  Belge konumunu Güvenilen konumlar listesine eklediğinizde veya özel olarak hata ayıklama ve yapı klasörlerini dahil ettiğinizde alt dizinleri ekleyin. Daha fazla bilgi için, [dosyalarınız için güvenilir bir konum oluşturma, kaldırma veya değiştirme](https://support.office.com/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62)Microsoft Office çevrimiçi yardım makalesini inceleyin.

### <a name="temporary-certificates"></a>Geçici sertifikalar
 İmzalama sertifikası zaten yoksa, Visual Studio geçici bir sertifika oluşturur. Bu geçici sertifikayı yalnızca geliştirme sırasında kullanmanız ve dağıtım için resmi bir sertifika satın almanız gerekir.

 Geçici sertifika, bir Office projesi ilk kez derlendikten sonra oluşturulur. **F5** tuşuna bastığınızda proje yeniden oluşturulur çünkü proje, sertifika eklendiğinde değişiklik olarak işaretlenir.

 Bir süre sonra çok sayıda geçici sertifika olabilir, bu nedenle geçici sertifikaları bazen temizlemeniz gerekir.

## <a name="visual-studio-tools-for-office-runtime"></a><a name="VisualStudioToolsForOfficeRuntime"></a> Office çalışma zamanı için Visual Studio Araçları
 , [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Yayımcının kimliğini ve bir özelleştirmeye verilen izinleri doğrulamak için özelliklere sahiptir. Bu izinleri bir dizi güvenlik denetimi aracılığıyla doğrular.

### <a name="security-during-customization-loading"></a>Özelleştirme yükleme sırasında güvenlik
 Belge düzeyi özelleştirmesi yüklendiğinde, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] her zaman belgenin güvenilir konumlar listesinde olup olmadığını denetler. Ayrıca, çalışma zamanı çözümün uygulama bildiriminde FullTrust isteyip istemediğini denetler. Özelleştirme yüklenirken ek bir güvenlik denetimi yapılmaz.

### <a name="sequence-of-security-checks-during-installation"></a>Yükleme sırasında güvenlik denetimlerinin sırası
 Bir Office çözümü yüklendiğinde veya güncelleştirilirken, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] güven kararı vermek için belirli bir sırada bir dizi güvenlik denetimi gerçekleştirir. Bir çözüm, yalnızca çalışma zamanı çözümün güvenilir olduğunu belirlerse yüklenir veya güncelleştirilir.

 Yükleme işlemini dört şekilde başlatabilirsiniz: Kurulum programını çalıştırarak, Microsoft Office uygulama konağını açarak veya *VSTOInstaller.exe* çalıştırarak dağıtım bildirimini açarak.

 İlk güvenlik denetimi yalnızca belge düzeyi çözümler için geçerlidir. Belge düzeyi çözümünün belgesi, güvenilir bir konumda olmalıdır. Belge, uzak bir ağ dosya paylaşımındaysa veya *. doc* veya *. docm* dosya adı uzantısına sahipse, belgenin konumu güvenilir konumlar listesine eklenmelidir. Daha fazla bilgi için bkz. [belgelere güven verme](../vsto/granting-trust-to-documents.md).

 ![VSTO güvenliği-Microsoft Office 'den yükleme](../vsto/media/host-install.png "VSTO güvenliği-Microsoft Office 'den yükleme")

 Sonraki güvenlik denetimleri kümesi [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ve ClickOnce ' dır. Bu denetimleri geçirmek için Office çözümlerinin FullTrust izinleri istemesi, güvenilmeyen yayımcı listesinde listelenmeyen bir sertifikayla imzalanması ve Internet Explorer kısıtlı bölgesinde olmayan bir konumda olması gerekir. Sertifika güvenilen yayımcı listesinde ise, çözüm hemen yüklenir. Aksi takdirde, denetimlerden biri başarısız olduysa, çözüm son denetim kümesine devam eder.

 ![Çözümleri yüklemeye yönelik VSTO güvenliği](../vsto/media/installing.png "Çözümleri yüklemeye yönelik VSTO güvenliği")

 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]Güven istemi 'ne izin veriliyorsa ve çözüme henüz güven verilmemişse, çalışma zamanı Son Kullanıcı tarafından güven kararının yapılmasına izin verir. Kullanıcı çözüme güven veriyorsa, Kullanıcı ekleme listesine bir giriş eklenir. Kullanıcı ekleme listesindeki tüm çözümler tam güvene sahiptir ve yüklenebilir ve çalıştırılabilir.

 Visual Studio 2010 ' den başlayarak, Office çözümü program dosyaları dizinine Windows Installer (MSI) kullanılarak yüklenirse ekleme listesi atlanır. Daha fazla bilgi için bkz. [ekleme listelerini kullanarak Office çözümlerine güvenme](../vsto/trusting-office-solutions-by-using-inclusion-lists.md).

 ![VSTO güvenliği-yüklemek için Kurulum programını kullanma](../vsto/media/setup-vstoinstaller.png "VSTO güvenliği-yüklemek için Kurulum programını kullanma")

## <a name="see-also"></a>Ayrıca bkz.

- [Office çözümlerine güven verme](../vsto/granting-trust-to-office-solutions.md)
- [Belgelere güven verme](../vsto/granting-trust-to-documents.md)
- [Ekleme listelerini kullanarak Office çözümlerine güvenme](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)
- [Nasıl yapılır: ekleme listesi güvenliğini yapılandırma](../vsto/how-to-configure-inclusion-list-security.md)
- [Nasıl yapılır: Office çözümlerini Imzalama](../vsto/how-to-sign-office-solutions.md)
- [Office çözüm güvenliği sorunlarını giderme](../vsto/troubleshooting-office-solution-security.md)
- [Office çözümleri için uygulama bildirimleri](../vsto/application-manifests-for-office-solutions.md)
- [Office çözümleri için dağıtım bildirimleri](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce Başvurusu](../deployment/clickonce-reference.md)
- [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)
