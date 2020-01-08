---
title: 'Nasıl yapılır: derleme günlüğü dosyalarını görüntüleme, kaydetme ve yapılandırma | Microsoft Docs'
ms.date: 08/28/2019
ms.technology: vs-ide-compile
ms.topic: conceptual
ms.assetid: 75d38b76-26d6-4f43-bbe7-cbacd7cc81e7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 923e8bb50b1caa323c602334c1d9a28b072043bd
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591326"
---
# <a name="how-to-view-save-and-configure-build-log-files"></a>Nasıl yapılır: derleme günlüğü dosyalarını görüntüleme, kaydetme ve yapılandırma

Visual Studio IDE 'de bir proje oluşturduktan sonra, bu yapı hakkındaki bilgileri **Çıkış** penceresinde görüntüleyebilirsiniz. Bu bilgileri kullanarak, örneğin, bir derleme hatası ile ilgili sorun giderme yapabilirsiniz. 

- Projeler C++ için Ayrıca, otomatik olarak oluşturulan ve kaydedilen bir *. txt* dosyasında aynı bilgileri de görebilirsiniz. 

- Yönetilen kod projeleri için, yapı çıkış penceresinde öğesine tıklayıp **Ctrl**+**S**' ye basabilirsiniz. Visual Studio, bilgileri **Çıkış** penceresinden bir *. txt* dosyasına kaydetmek için size bir konum sorar. 

Ayrıca, her derleme hakkında görüntülemek istediğiniz bilgi türlerini belirtmek için IDE 'yi de kullanabilirsiniz.

MSBuild kullanarak herhangi bir tür proje oluşturuyorsanız, derleme hakkında bilgi kaydetmek için bir *. txt* dosyası oluşturabilirsiniz. Daha fazla bilgi için bkz. [Derleme günlüklerini alma](../msbuild/obtaining-build-logs-with-msbuild.md).

## <a name="to-view-the-build-log-file-for-a-c-project"></a>Bir C++ projenin derleme günlük dosyasını görüntülemek için

1. **Windows Gezgini** veya **Dosya Gezgini**'nde şu dosyayı açın: *\\. ..\adim Studio \<sürüm\>\projects\\< projectname\>\\< projectname\>\debug\\< ProjectName\>. txt*

## <a name="to-create-a-build-log-file-for-a-managed-code-project"></a>Yönetilen kod projesi için bir yapı günlük dosyası oluşturmak için

1. Menü çubuğunda **derleme** > **Build Solution**' ı seçin.

2. **Çıkış** penceresinde, metinde herhangi bir yere tıklayın.

3. **Ctrl**+**S**tuşlarına basın.

   Visual Studio, derleme çıktısının kaydedileceği bir konum ister.

Ayrıca, `-fileLogger` (`-fl`) komut satırı seçeneğini kullanarak doğrudan komut satırından MSBuild 'i çalıştırarak da Günlükler oluşturabilirsiniz. Bkz. [MSBuild ile derleme günlükleri alma](../msbuild/obtaining-build-logs-with-msbuild.md).

## <a name="to-change-the-amount-of-information-included-in-the-build-log"></a>Yapı günlüğünde bulunan bilgi miktarını değiştirmek için

1. Menü çubuğunda, **Araçları** > **seçenekleri**.

2. **Projeler ve çözümler** sayfasında, **derleme ve çalıştırma** sayfasını seçin.

3. **MSBuild proje derleme çıkışı ayrıntı** listesinde, aşağıdaki değerlerden birini seçin ve ardından **Tamam** düğmesini seçin.

    |Ayrıntı düzeyi|Açıklama|
    | - |-----------------|
    |**Sess**|Yalnızca yapı özetini görüntüler.|
    |**En az**|Derleme ve hataların, uyarıların ve son derece önemli olarak sınıflandırılan mesajların özetini görüntüler.|
    |**Olağan**|Derleme özetini görüntüler; yüksek oranda önemli olarak sınıflandırılan hatalar, uyarılar ve iletiler ve yapı ana adımları. En sık bu ayrıntı düzeyini kullanacaksınız.|
    |**Ayrıntılı**|Derleme özetini görüntüler; yüksek oranda önemli olarak sınıflandırılan hatalar, uyarılar ve iletiler Tüm Yapı adımları; ve normal önem derecesine göre sınıflandırılan mesajlar.|
    |**Tanı**|Yapı için kullanılabilen tüm verileri görüntüler. Özel derleme betiklerine ve diğer yapı sorunlarıyla ilgili sorunları ayıklamanıza yardımcı olması için bu ayrıntı düzeyini kullanabilirsiniz.|

     Daha fazla bilgi için bkz. [Seçenekler iletişim kutusu, projeler ve çözümler, derleme ve çalıştırma](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md) ve <xref:Microsoft.Build.Framework.LoggerVerbosity>.

    > [!IMPORTANT]
    > Değişikliklerinizin **Çıkış** penceresinde (tüm projeler) ve *\<ProjectName >. txt* dosyasında (C++ yalnızca projeler) etkili olması için projeyi yeniden oluşturmanız gerekir.

## <a name="use-binary-logs-to-make-it-easier-to-browse-large-log-files"></a>Büyük günlük dosyalarına gözatmaya daha kolay hale getirmek için ikili günlükleri kullanın

İkili Günlükler, büyük günlüklerde bilgi bulmayı kolaylaştıran daha zengin bir günlük tarama deneyimine sahip olmanızı sağlayan, .NET projeleri için isteğe bağlı bir özelliktir. İkili günlükleri kullanmak için, [Proje sistemi araçları](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.ProjectSystemTools)'nı yükler. Daha fazla bilgi için bkz. [https://msbuildlog.com](https://msbuildlog.com) ve [ikili günlük](https://github.com/microsoft/msbuild/blob/master/documentation/wiki/Binary-Log.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da projeler ve çözümler oluşturma ve Temizleme](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Derleme ve oluşturma](../ide/compiling-and-building-in-visual-studio.md)
