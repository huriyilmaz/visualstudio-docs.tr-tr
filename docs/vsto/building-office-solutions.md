---
title: Office çözümleri oluşturun
description: Office projeleri oluşturma ve hata ayıklama ile Windows Forms gibi Visual Studio diğer proje türlerini oluşturma ve hata ayıklama arasındaki farkları öğrenin.
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
ms.openlocfilehash: f47b429bdb0ab5275718f45c29c0627cb143efa42e3e275c6d9ff1b82e39cb33
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121299038"
---
# <a name="build-office-solutions"></a>Office çözümleri oluşturun
  genel olarak, Office projeler derleme ve hata ayıklama ile Visual Studio Windows Forms gibi diğer proje türlerini derleme ve hata ayıklama ile aynıdır. Bu bölümdeki konular, var olan farkları açıklamaktadır. Uygulamaları oluşturma hakkında genel bilgi için, bkz. [Visual Studio derleme ve derleme](../ide/compiling-and-building-in-visual-studio.md).

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="project-output-for-office-projects"></a>Office projeleri için Project çıkışı
 Office projeler için çıkış konumu *projectname*\bin\release veya *projectname*\bin\debug' dir. Dağıtım dizinine derlenemez.

### <a name="document-level-projects"></a>Belge düzeyi projeleri
 Belge düzeyinde bir proje oluşturduğunuzda, aşağıdaki öğeler proje çıktısına dahil edilir:

- Proje belgesinin bir kopyası.

- Proje derlemesi ve **Copy Local** özelliği **true** olarak ayarlanmış olan tüm başvurulan derlemeler.

- Dosya adı uzantısı *. manifest* olan uygulama bildirimi. daha fazla bilgi için bkz. [Office çözümleri için uygulama bildirimleri](../vsto/application-manifests-for-office-solutions.md).

- *. VSTO* dosya adı uzantısına sahip dağıtım bildirimi. daha fazla bilgi için bkz. [Office çözümleri için dağıtım bildirimleri](../vsto/deployment-manifests-for-office-solutions.md).

- Program veritabanı (*pdb*) dosyası.

> [!NOTE]
> Yerel bilgisayar yerine uzak bir konuma belge düzeyinde bir çözüm oluşturursanız, uygulamanın güven merkezindeki güvenilir konumlar listesine tam yolu ekleyin. daha fazla bilgi için [güvenli Office çözümlerinde](../vsto/securing-office-solutions.md)belgelere güven verme adlı bölüme bakın.

### <a name="application-level-projects"></a>Uygulama düzeyi projeleri
 VSTO bir eklenti projesi oluşturduğunuzda, aşağıdaki öğeler proje çıktısına dahil edilir:

- Proje derlemesi ve **Copy Local** özelliği **true** olarak ayarlanmış olan tüm başvurulan derlemeler.

- Dosya adı uzantısı *. manifest* olan uygulama bildirimi. daha fazla bilgi için bkz. [Office çözümleri için uygulama bildirimleri](../vsto/application-manifests-for-office-solutions.md).

- *. VSTO* dosya adı uzantısına sahip dağıtım bildirimi. daha fazla bilgi için bkz. [Office çözümleri için dağıtım bildirimleri](../vsto/deployment-manifests-for-office-solutions.md).

- Proje derlemesi için bir program veritabanı (*pdb*) dosyası.

  VSTO eklentisi projeleri için derleme işlemi, geliştirme bilgisayarında VSTO eklentisini yüklemek için gereken bir kayıt defteri girişleri kümesi de oluşturur. daha fazla bilgi için bkz. [VSTO eklentileri için kayıt defteri girişleri](../vsto/registry-entries-for-vsto-add-ins.md).

  form bölgelerini içeren bir Outlook VSTO eklentisi projesi oluşturursanız, yapı işlemi kayıt defterine aşağıdaki ek bilgileri ekler:

- Bir veya daha fazla form bölgesi ile ilişkili her ileti sınıfı için bir anahtar.

- her form bölgesi için bir giriş ve Outlook VSTO eklentisinin adını temsil eden ilişkili bir değer.

  Outlook, form bölgelerini yüklemek için bu bilgiye ihtiyaç duyuyor.

## <a name="referenced-assemblies"></a>Başvurulan derlemeler
 derlemelere (sınıf kitaplığı projeleri dahil), yapı Office çözümleri projenizden başvurabilirsiniz. Her Başvurulmuş derleme **Yerel kopyalama** adlı bir özelliğe sahiptir. Yereli **Kopyala** , derlemenin çıkış dizinine kopyalanıp kopyalanmadığını gösterir. Varsayılan olarak **true** değerine ayarlanır. Yereli **Kopyala** ayarı **true** olan her Başvurulmuş derleme çıkış dizinine kopyalanır.

## <a name="security-during-the-build-process"></a>Oluşturma işlemi sırasında güvenlik
 Visual Studio, derleme işlemi sırasında çözüme güven sağlamak için geliştirme bilgisayarındaki güvenlik ayarlarını otomatik olarak yapılandırır. Bu, çözümün hata ayıklarken çalışmasına izin verir.

 Office projeler, yayımcıyı doğrulamak için sertifikaları kullanır. Visual Studio, Office çözümlerini belirlemek için otomatik olarak geçici bir sertifika oluşturur ve geliştirme bilgisayarını geçici sertifikaya güvenecek şekilde yapılandırır.

 daha fazla bilgi için bkz. [Secure Office solutions](../vsto/securing-office-solutions.md).

### <a name="network-projects"></a>Ağ projeleri
 Derleme veya belge konumu bir ağ paylaşımındaysa, yerel (Kullanıcı düzeyi) güvenlik ilkesi güncelleştirmesi çözümün çalışmasına izin vermek için yeterli değildir. Bir yönetici, çözüm çalıştırılmadan önce bir ağ paylaşımındaki derlemeler ve belgeler için makine düzeyinde tam güven vermelidir. güvenlik ilkesini ayarlama hakkında daha fazla bilgi için bkz. [Secure Office solutions](../vsto/securing-office-solutions.md).

 belge düzeyi projeleri için, ayrıca, belgenin tam konumunu Office güvenilir klasörler listesine eklemeniz gerekir. Daha fazla bilgi için bkz. [belgelere güven verme](../vsto/granting-trust-to-documents.md).

## <a name="change-the-platform-target"></a>Platform hedefini değiştirme
 varsayılan olarak, Office projeler için platform hedefi **herhangi bir CPU** olur. Genellikle, bu ayarı değiştirmemelisiniz. **herhangi bir CPU** platformu hedefi ayarıyla oluşturulan Office çözümler, Microsoft 'un 32-bit ve 64-bit sürümlerinde çalışır [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] .

 Platform hedefini yalnızca Microsoft 'un 64-bit sürümlerinde çalışacak bir çözüm oluşturuyorsanız [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] ve çözümünüz yerel 64 bit API 'leri çağırdığında x64 olarak ayarlamanız gerekir. Platform hedefi ayarını değiştirme hakkında daha fazla bilgi için bkz. [nasıl yapılır: projeleri hedef platformları Için yapılandırma](../ide/how-to-configure-projects-to-target-platforms.md).

 platform hedefini x64 olarak ayarlarsanız, çözüm Windows veya Office 32 bitlik sürümlerinde çalışmaz. X64 platformu hedefi, çözümün 64 bitlik bir işlemde çalıştırılmasını gerektirir.

## <a name="use-the-clean-command"></a>Temizle komutunu kullanma
 Oluşturulan proje dosyalarını geliştirme bilgisayarından kaldırmak için içindeki **derleme** menüsündeki **Temizle** komutunu kullanabilirsiniz [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . **Clean** komutu derleme çıkış konumundaki tüm dosyaları siler. Uygulama düzeyi projeleri için, **Temizleme** komutu yapı işlemi tarafından oluşturulan kayıt defteri girişlerini de kaldırır.

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Office projelerinde hata ayıklama](../vsto/debugging-office-projects.md)|Office projelerinde hata ayıklama ile ilgili sorunları gösterir.|
|[İzlenecek yol: Excel için ilk belge düzeyi özelleştirmeyi oluşturma](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)|Excel için temel bir belge düzeyi özelleştirmesi oluşturmayı gösterir.|
|[nasıl yapılır: devre dışı bırakılmış bir VSTO eklentisini yeniden etkinleştirme](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)|zor veya geçici olarak devre dışı bırakılmış bir VSTO eklentisinin nasıl yeniden etkinleştirileceğini açıklar.|
|[Office çözümleri tasarlama ve oluşturma](../vsto/designing-and-creating-office-solutions.md)|Office çözümleri oluşturma ve çözümünüzde derlemelerin rolü hakkında bilgi için bağlantılar sağlar.|