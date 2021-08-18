---
title: Güvenli Office çözümleri
description: Office çözümleri için güvenlik modelinin çalışma zamanı ve çalışma zamanı gibi Office için Visual Studio Araçları teknolojileri nasıl ClickOnce.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122115063"
---
# <a name="secure-office-solutions"></a>Güvenli Office çözümleri
  Office çözümleri için güvenlik modeli çeşitli teknolojiler içerir: , , Microsoft Office Güven Merkezi ve [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] Internet Explorer sınırlı siteler bölgesi. Aşağıdaki bölümlerde, farklı güvenlik özelliklerinin nasıl işlen olduğu açıklanmaktadır:

- [Çözüme güven Office ver](#GrantingTrustToSolutions)

- [Belgelere güven izni ver](#GrantingTrustToDocuments)

- [Windows Installer kullanırken güven izni ver](#GrantingTrustWindowsInstaller)

- [Güvenlik çözümleri için belirli güvenlik Office dikkat edilmesi gerekenler](#Security)

- [Geliştirme sırasında güvenlik](#SecurityDuringDeployment)

- [Office çalışma zamanı için Visual Studio Araçları](#VisualStudioToolsForOfficeRuntime)

  [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="grant-trust-to-office-solutions"></a><a name="GrantingTrustToSolutions"></a>Çözüme güven Office ver
 Çözüme güven Office vermek, aşağıdaki kanıta dayanarak her son kullanıcının güvenlik Office çözümüne güvenerek değiştirme anlamına gelir:

- Dağıtım bildirimini imzalamak için kullanılan sertifika.

- Dağıtım bildiriminin URL'si.

  Daha fazla bilgi için, [bkz. Grant trust to Office solutions](../vsto/granting-trust-to-office-solutions.md).

## <a name="grant-trust-to-documents"></a><a name="GrantingTrustToDocuments"></a> Belgelere güven izni ver
 Belge düzeyinde özelleştirme, belgenin güvenilir konum olarak belirlenen bir dizinde olması gerekir. Daha fazla bilgi için [bkz. Belgelere güven izni ver.](../vsto/granting-trust-to-documents.md)

## <a name="grant-trust-when-using-windows-installer"></a><a name="GrantingTrustWindowsInstaller"></a>Windows Installer'ı kullanırken güven izni ver
 Windows Yükleyicisi'nde yönetici hakları gerektiren Program Files dizinine Office bir MSI dosyası oluşturabilirsiniz. Program Files dizininde Office çözümleri için Visual Studio 2010 Tools for Office runtime, bu Office çözümlerinin güvenilir olduğunu kabul ediyor ve ClickOnce güven istemini göstermemektedir.

## <a name="specific-security-considerations-for-office-solutions"></a><a name="Security"></a>Güvenlik çözümleri için belirli güvenlik Office dikkat edilmesi gerekenler
 , ve tarafından sağlanan güvenlik özellikleri Microsoft Office çözümlerinin çeşitli olası güvenlik tehditlerine karşı koruma [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] Office olabilir. Daha fazla bilgi için [bkz. Güvenlik çözümleriyle ilgili Office dikkat edilmesi gerekenler.](../vsto/specific-security-considerations-for-office-solutions.md)

## <a name="security-during-development"></a><a name="SecurityDuringDeployment"></a> Geliştirme sırasında güvenlik
 Geliştirme sürecinizi kolaylaştırmak için Visual Studio proje bilgisayarınızda her bilgisayarınızda çalıştırmak ve hata ayıklamak için gereken güvenlik ilkesi ayarlar. Bazı senaryolarda projeyi geliştirmek için ek güvenlik adımlarına ihtiyacınız olabilir.

### <a name="document-level-solutions"></a>Belge düzeyi çözümler
 Bir belgenin tam yolu, aşağıdaki proje türlerini geliştiriyorsanız Microsoft Office uygulamanın güvenilir konumlar listesine eklenmiştir:

- *\\ \servername\sharename* gibi bir ağ dosya paylaşımında olan belge düzeyi çözümler.

- .doc *veya .docm* *dosyalarını kullanan* Word için belge düzeyi çözümler.

  Belge konumunu güvenilen konumlar listesine eklerken veya özellikle hata ayıklama ve derleme klasörleri eklerken alt dizinleri ekleyin. Daha fazla bilgi için çevrimiçi Microsoft Office dosyalarınız için güvenilen bir konum oluşturma, kaldırma veya değiştirme [makalesine bakın.](https://support.office.com/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62)

### <a name="temporary-certificates"></a>Geçici sertifikalar
 Visual Studio imzalama sertifikası yoksa geçici bir sertifika oluşturur. Bu geçici sertifikayı yalnızca geliştirme sırasında kullanmalısınız ve dağıtım için resmi bir sertifika satın alın.

 Geçici sertifika, bir proje Office sonra oluşturulur. **F5** tuşuna bir sonraki basında, proje sertifika eklenirken değiştirilmiş olarak işaretlenir çünkü proje yeniden oluşturulur.

 Bir süre sonra çok sayıda geçici sertifika olabilir, bu nedenle ara sıra geçici sertifikaları temizlemelisiniz.

## <a name="visual-studio-tools-for-office-runtime"></a><a name="VisualStudioToolsForOfficeRuntime"></a>Office için Visual Studio Araçları çalışma zamanı
 , [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] yayımcının kimliğini ve özelleştirmeye verilen izinleri doğrulama özelliklerine sahiptir. Bu izinleri bir dizi güvenlik denetimiyle doğrular.

### <a name="security-during-customization-loading"></a>Özelleştirme yüklemesi sırasında güvenlik
 Belge düzeyinde özelleştirme yüklendiğinde, her zaman [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] belgenin güvenilen konumlar listesinde olup olmadığını denetler. Ayrıca çalışma zamanı, çözümün uygulama bildiriminde FullTrust isteğinde olup olmadığını denetler. Özelleştirme yüklenirken ek güvenlik denetimi gerçekleştirin.

### <a name="sequence-of-security-checks-during-installation"></a>Yükleme sırasında güvenlik denetimleri dizisi
 Bir Office veya güncelleştirildiğinde, güven kararı için belirli bir dizi [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] güvenlik denetimi gerçekleştirir. Yalnızca çalışma zamanı çözümün güvenilir olduğunu belirlerse bir çözüm yüklenir veya güncelleştirilir.

 Yükleme işlemini dört şekilde başlatabilirsiniz: Kurulum programını çalıştırarak, dağıtım bildirimini açarak, Microsoft Office uygulama ana bilgisayarını açarak veya *VSTOInstaller.exe.*

 İlk güvenlik denetimi yalnızca belge düzeyi çözümler için geçerlidir. Belge düzeyi çözümün belgesi güvenilir bir konumda yer alalır. Belge bir uzak ağ dosya paylaşımında veya *.doc* *veya .docm* dosya adı uzantısına sahipse, belgenin konumu güvenilen konumlar listesine eklenmiştir. Daha fazla bilgi için [bkz. Belgelere güven izni ver.](../vsto/granting-trust-to-documents.md)

 ![VSTO güvenliği - Microsoft Office'den yükleme](../vsto/media/host-install.png "VSTO güvenliği - Microsoft Office'den yükleme")

 Sonraki güvenlik denetimleri kümesi ve [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ClickOnce. Bu denetimlerin başarılı olması için Office çözümlerinin Tam Güven izinleri isteğinde olması, Güvenilmeyen Publisher listesinde yer alan bir sertifikayla imzalanmış olması ve Internet Explorer kısıtlanmış bölgede olmayan bir konumda olması gerekir. Sertifika Güvenilen sertifika listesinde Publisher çözüm hemen yüklenir. Aksi takdirde, denetimlerden biri başarısız olmazsa çözüm son denetim kümesine devam eder.

 ![VSTO yüklemek için güvenlik](../vsto/media/installing.png "VSTO yüklemek için güvenlik")

 Güven istemine izin verilirse ve çözüme henüz güven verilmemişse, çalışma zamanı son kullanıcı tarafından güven [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] kararı verilmesine izin verecek. Kullanıcı çözüme güven izni verdiyse, kullanıcı ekleme listesine bir giriş eklenir. Kullanıcı ekleme listesinde yer alan tüm çözümler tam güvene sahiptir ve yüklerini yükp çalıştırabilirsiniz.

 Visual Studio 2010'dan başlayarak, Office çözümü Program Dosyaları dizinine Windows Yükleyicisi (MSI) kullanılarak yüklenirse ekleme listesi atlanır. Daha fazla bilgi için [bkz. Office kullanarak güven ve çözümlere güven.](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)

 ![VSTO güvenlik - yüklemek için Kurulum programını kullanma](../vsto/media/setup-vstoinstaller.png "VSTO güvenlik - yüklemek için Kurulum programını kullanma")

## <a name="see-also"></a>Ayrıca bkz.

- [Çözüme güven Office ver](../vsto/granting-trust-to-office-solutions.md)
- [Belgelere güven izni ver](../vsto/granting-trust-to-documents.md)
- [Dahil Office kullanarak çözüme güvenin](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)
- [Nasıl yapılandırılır: Ekleme listesi güvenliğini yapılandırma](../vsto/how-to-configure-inclusion-list-security.md)
- [Nasıl Office: Office imzalama](../vsto/how-to-sign-office-solutions.md)
- [Çözüm Office sorunlarını giderme](../vsto/troubleshooting-office-solution-security.md)
- [Uygulama çözümleri için Office bildirimleri](../vsto/application-manifests-for-office-solutions.md)
- [Dağıtım çözümleri için Office bildirimleri](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce başvurusu](../deployment/clickonce-reference.md)
- [Bir Office dağıtma](../vsto/deploying-an-office-solution.md)
