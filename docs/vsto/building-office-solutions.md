---
title: Yeni Office oluşturma
description: Office Forms gibi Visual Studio ve hata ayıklama arasındaki fark Windows ları öğrenin.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- debugging [Office development in Visual Studio]
- debugging Office applications in Visual Studio
- solutions [Office development in Visual Studio], debugging
- Office applications [Office development in Visual Studio], debugging
- application development [Office development in Visual Studio], building
- Office applications [Office development in Visual Studio], building
- projects [Office development in Visual Studio], debugging
- Office solutions [Office development in Visual Studio], building
- solutions [Office development in Visual Studio], building
- Office projects [Office development in Visual Studio], debugging
- projects [Office development in Visual Studio], building
- builds [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], building
- application development [Office development in Visual Studio], debugging
- Office solutions [Office development in Visual Studio], debugging
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: d31bcb5c74e4ce4b6049daff868ede2811108e79
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122047172"
---
# <a name="build-office-solutions"></a>Yeni Office oluşturma
  Genel olarak, Office projelerinin Visual Studio ve hata ayıklaması, Visual Studio Forms gibi diğer proje türlerini Windows aynıdır. Bu bölümdeki konular, mevcut olan farkları açıklar. Uygulama derleme hakkında genel bilgi için bkz. Derleme [ve derleme Visual Studio.](../ide/compiling-and-building-in-visual-studio.md)

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="project-output-for-office-projects"></a>Project projeleri için Office çıktısı
 Projelerin çıkış Office *projeadı*\bin\release veya *projeadı*\bin\debug'dır. Bir dağıtım dizinine derleme yapılaamaz.

### <a name="document-level-projects"></a>Belge düzeyi projeler
 Belge düzeyinde bir proje derlemeniz, proje çıkışına aşağıdaki öğeler dahil edilir:

- Proje belgesinin bir kopyası.

- Proje derlemesi ve Yereli Kopyala özelliği true olarak ayarlanmış **başvurulan** tüm **derlemeler.**

- .manifest dosya adı uzantısına sahip uygulama *bildirimi.* Daha fazla bilgi için [bkz. Uygulama çözümleri için Office bildirimleri.](../vsto/application-manifests-for-office-solutions.md)

- .vsto dosya adı uzantısına sahip *dağıtım bildirimi.* Daha fazla bilgi için [bkz. Çözüm için Office bildirimleri.](../vsto/deployment-manifests-for-office-solutions.md)

- Bir program veritabanı (*PDB*) dosyası.

> [!NOTE]
> Yerel bilgisayar yerine uzak bir konuma belge düzeyinde bir çözüm derlemeniz, uygulamanın Güven Merkezi'nde Güvenilen Konumlar listesine tam yolu ekleyin. Daha fazla bilgi için Güvenli Çözümlerde Belgelere Güven Office [bakın.](../vsto/securing-office-solutions.md)

### <a name="application-level-projects"></a>Uygulama düzeyindeki projeler
 Bir Eklenti VSTO derlemeniz, proje çıkışına aşağıdaki öğeler dahil edilir:

- Proje derlemesi ve Yereli Kopyala özelliği true olarak ayarlanmış **başvurulan** tüm **derlemeler.**

- .manifest dosya adı uzantısına sahip uygulama *bildirimi.* Daha fazla bilgi için [bkz. Uygulama çözümleri için Office bildirimleri.](../vsto/application-manifests-for-office-solutions.md)

- .vsto dosya adı uzantısına sahip *dağıtım bildirimi.* Daha fazla bilgi için [bkz. Çözüm için Office bildirimleri.](../vsto/deployment-manifests-for-office-solutions.md)

- Proje derlemesi için bir program veritabanı (*PDB*) dosyası.

  Eklenti projelerinin VSTO işlemi, geliştirme bilgisayarda eklentiyi yüklemek için gereken bir kayıt defteri girdileri VSTO oluşturur. Daha fazla bilgi için [bkz. Eklentilerini VSTO kayıt defteri girdileri.](../vsto/registry-entries-for-vsto-add-ins.md)

  Form bölgelerini içeren Outlook VSTO bir Eklenti projesi oluşturursanız, derleme işlemi kayıt defterine aşağıdaki ek bilgileri ekler:

- Bir veya daha fazla form bölgesiyle ilişkili her ileti sınıfı için bir anahtar.

- Her form bölgesi için bir giriş ve eklentinin adını temsil eden ilişkili Outlook VSTO.

  Outlook bölgeleri yüklemek için bu bilgilere ihtiyaç vardır.

## <a name="referenced-assemblies"></a>Başvurulan derlemeler
 Derlemelere (sınıf kitaplığı projeleri dahil) Building Office Solutions projenize başvurabilirsiniz. Başvurulan her derlemenin Yereli Kopyala adlı **bir özelliği vardır.** **Yerel Kopyala,** derlemenin çıkış dizinine kopyalayıp kopyalan olmadığını gösterir. Varsayılan olarak true olarak **ayarlanır.** Yereli Kopyala'nın **true** **olarak ayarlanmış** olduğu başvurulan her derleme, çıkış dizinine kopyalanır.

## <a name="security-during-the-build-process"></a>Derleme işlemi sırasında güvenlik
 Visual Studio, derleme işlemi sırasında çözüme güven vermek için geliştirme bilgisayarında güvenlik ayarlarını otomatik olarak yapılandırıyor. Bu, siz hata ayıklarken çözümün çalışmasına olanak sağlar.

 Office projeleri yayımcıyı doğrulamak için sertifikaları kullanır. Visual Studio çözümlerini tanımlamak için otomatik olarak geçici bir Office oluşturur ve geliştirme bilgisayarı geçici sertifikaya güven olacak şekilde yapılandırmaktadır.

 Daha fazla bilgi için [bkz. Güvenli Office çözümleri.](../vsto/securing-office-solutions.md)

### <a name="network-projects"></a>Ağ projeleri
 Derleme veya belge konumu bir ağ paylaşımında ise, çözümün çalışmasına izin vermek için yerel (Kullanıcı düzeyi) güvenlik ilkesi güncelleştirmesi yeterli değildir. Yöneticinin, çözümün çalışmadan önce ağ paylaşımında yer alan derlemelere ve belgelere Makine düzeyinde tam güven iznini olması gerekir. Güvenlik ilkesi ayarlama hakkında daha fazla bilgi için bkz. [Güvenlik Office.](../vsto/securing-office-solutions.md)

 Belge düzeyindeki projeler için, belgenin tam konumunu da güvenilir klasörler listesine Office gerekir. Daha fazla bilgi için [bkz. Belgelere güven izni ver.](../vsto/granting-trust-to-documents.md)

## <a name="change-the-platform-target"></a>Platform hedefini değiştirme
 Varsayılan olarak, herhangi bir CPU Office platform **hedefidir.** Genellikle, bu ayarı değiştirmeyebilirsiniz. Office herhangi bir **CPU** platformu hedefi ayarıyla 32 bit ve 64 bit Microsoft veya sürümlerinde çalıştır edilen tüm [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] çözümler.

 Yalnızca Microsoft veya 'nin yalnızca 64 bit sürümlerinde çalıştıracak bir çözüm oluşturuyorsanız ve çözümünüz yerel 64 bit API'leri çağırıyorsa platform hedefini [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] x64 olarak ayarlayabilirsiniz. Platform hedef ayarını değiştirme hakkında daha fazla bilgi için [bkz. Nasıl yapılandırılır: Projeleri platformları hedef olarak yapılandırma.](../ide/how-to-configure-projects-to-target-platforms.md)

 Platform hedefini x64 olarak ayarsanız çözüm, Windows veya Office'nin 32 bit sürümlerinde Windows. x64 platform hedefi, çözümün 64 bit bir işlemde çalışması gerekir.

## <a name="use-the-clean-command"></a>Clean komutunu kullanma
 Derleme proje dosyalarını geliştirme bilgisayarından kaldırmak için, içinde Derleme **menüsündeki Temizle** **komutunu** [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] kullanabilirsiniz. Temiz **komutu,** derleme çıkış konumu içinde yer alan tüm dosyaları siler. Uygulama düzeyindeki projelerde **Clean** komutu derleme işlemi tarafından oluşturulan kayıt defteri girdilerini de kaldırır.

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Projelerde Office ayıklama](../vsto/debugging-office-projects.md)|Projelerde hata ayıklamayla ilgili Office sunar.|
|[Adım adım kılavuz: Belge düzeyi için ilk belge düzeyi özelleştirmenizi Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)|Uygulama için temel bir belge düzeyi özelleştirmesi oluşturma Excel.|
|[Nasıl: Devre dışı bırakılmış VSTO Eklentiyi yeniden etkinleştirme](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)|Sabit veya yazılımlı devre dışı bırakılmış VSTO Bir Eklentiyi yeniden etkinleştirmeyi açıklar.|
|[Yeni çözümler tasarlama Office oluşturma](../vsto/designing-and-creating-office-solutions.md)|Tek bir çözüm oluşturma ve Office derlemelerin rolü hakkında bilgi bağlantıları sağlar.|