---
title: 'Nasıl yapılır: derleme günlüğü dosyalarını görüntüleme, kaydetme ve yapılandırma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 75d38b76-26d6-4f43-bbe7-cbacd7cc81e7
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ffc1c620136c55c42f3468129ed164075d762bff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670502"
---
# <a name="how-to-view-save-and-configure-build-log-files"></a>Nasıl yapılır: Derleme Günlüğü Dosyalarını Görüntüleme, Kaydetme ve Yapılandırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio IDE 'de bir proje oluşturduktan sonra, bu yapı hakkındaki bilgileri **Çıkış** penceresinde görüntüleyebilirsiniz. Bu bilgileri kullanarak, örneğin, bir derleme hatası ile ilgili sorun giderme yapabilirsiniz. C++ projeleri için aynı bilgileri, otomatik olarak oluşturulup kaydedilen bir. txt dosyasında da görüntüleyebilirsiniz. Yönetilen kod projeleri için, **Çıkış** penceresindeki bilgileri kopyalayıp bir. txt dosyasına yapıştırabilir ve kendiniz kaydedebilirsiniz. Ayrıca, her derleme hakkında görüntülemek istediğiniz bilgi türlerini belirtmek için IDE 'yi de kullanabilirsiniz.

 MSBuild kullanarak herhangi bir tür proje oluşturuyorsanız, derleme hakkında bilgi kaydetmek için bir. txt dosyası oluşturabilirsiniz. Daha fazla bilgi için bkz. [Derleme günlüklerini alma](../msbuild/obtaining-build-logs-with-msbuild.md).

### <a name="to-view-the-build-log-file-for-a-c-project"></a>Bir C++ projesi için derleme günlük dosyasını görüntülemek için

1. **Windows Gezgini** veya **Dosya Gezgini**içinde şu dosyayı açın: \\ . ..\Adim Studio *Sürüm*\projects \\ *ProjectName* \\ *ProjectName*\debug \\ *ProjectName*. txt

### <a name="to-create-a-build-log-file-for-a-managed-code-project"></a>Yönetilen kod projesi için bir yapı günlük dosyası oluşturmak için

1. Menü çubuğunda **Oluştur**, **çözüm oluştur**' u seçin.

2. **Çıkış** penceresinde, derlemeden bilgileri vurgulayın ve panoya kopyalayın.

3. Not Defteri gibi bir metin Düzenleyicisi açın, bilgileri dosyaya yapıştırın ve kaydedin.

### <a name="to-change-the-amount-of-information-included-in-the-build-log"></a>Yapı günlüğünde bulunan bilgi miktarını değiştirmek için

1. Menü çubuğunda **Araçlar**, **Seçenekler**' i seçin.

2. **Projeler ve çözümler** sayfasında, **derleme ve çalıştırma** sayfasını seçin.

3. **MSBuild proje derleme çıkışı ayrıntı** listesinde, aşağıdaki değerlerden birini seçin ve ardından **Tamam** düğmesini seçin.

    |Ayrıntı düzeyi|Açıklama|
    |---------------------|-----------------|
    |Quiet|Yalnızca yapı özetini görüntüler.|
    |En az|Derleme ve hataların, uyarıların ve son derece önemli olarak sınıflandırılan mesajların özetini görüntüler.|
    |Normal|Derleme özetini görüntüler; yüksek oranda önemli olarak sınıflandırılan hatalar, uyarılar ve iletiler ve yapı ana adımları. En sık bu ayrıntı düzeyini kullanacaksınız.|
    |Ayrıntılı|Derleme özetini görüntüler; yüksek oranda önemli olarak sınıflandırılan hatalar, uyarılar ve iletiler Tüm Yapı adımları; ve normal önem derecesine göre sınıflandırılan mesajlar.|
    |Tanılama|Yapı için kullanılabilen tüm verileri görüntüler. Özel derleme betiklerine ve diğer yapı sorunlarıyla ilgili sorunları ayıklamanıza yardımcı olması için bu ayrıntı düzeyini kullanabilirsiniz.|

     Daha fazla bilgi için bkz. [Seçenekler Iletişim kutusu, projeler ve çözümler, oluşturma ve çalıştırma](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md) <xref:Microsoft.Build.Framework.LoggerVerbosity> .

    > [!IMPORTANT]
    > Değişikliklerinizin **Çıkış** penceresinde (tüm projeler) ve *ProjectName*. txt dosyasında (yalnızca C++ projeleri) etkili olması için projeyi yeniden oluşturmanız gerekir.

## <a name="see-also"></a>Ayrıca Bkz.
 Visual Studio [derleme ve oluşturma](../ide/compiling-and-building-in-visual-studio.md) ile [Proje ve çözüm oluşturma ve Temizleme](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md) , [derleme günlükleri alma](../msbuild/obtaining-build-logs-with-msbuild.md)
