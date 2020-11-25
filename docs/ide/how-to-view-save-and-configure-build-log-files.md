---
title: 'Nasıl yapılır: derleme günlüğü dosyalarını görüntüleme, kaydetme ve yapılandırma | Microsoft Docs'
description: Derleme günlüğü dosyalarını görüntüleme, kaydetme ve yapılandırma hakkında bilgi edinin. Bu dosyalar, derleme hatasına sorun giderme gibi görevler için yararlı bilgiler sağlar.
ms.custom: SEO-VS-2020
ms.date: 08/28/2019
ms.technology: vs-ide-compile
ms.topic: how-to
ms.assetid: 75d38b76-26d6-4f43-bbe7-cbacd7cc81e7
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 02d26416357ec13b61232f2adb0bc3e5e3c67818
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "95970201"
---
# <a name="how-to-view-save-and-configure-build-log-files"></a>Nasıl yapılır: derleme günlüğü dosyalarını görüntüleme, kaydetme ve yapılandırma

Visual Studio IDE 'de bir proje oluşturduktan sonra, bu yapı hakkındaki bilgileri **Çıkış** penceresinde görüntüleyebilirsiniz. Bu bilgileri kullanarak, örneğin, bir derleme hatası ile ilgili sorun giderme yapabilirsiniz.

- C++ projeleri için aynı bilgileri bir proje oluşturduğunuzda oluşturulup kaydettiğiniz bir günlük dosyasında da görüntüleyebilirsiniz. 

- Yönetilen kod projeleri için, derleme çıkış penceresinde ' ne tıklayabilir ve **CTRL** + **S**' ye basabilirsiniz. Visual Studio, bilgileri **Çıkış** penceresinden bir günlük dosyasına kaydetmek için size bir konum sorar.

Ayrıca, her derleme hakkında görüntülemek istediğiniz bilgi türlerini belirtmek için IDE 'yi de kullanabilirsiniz.

MSBuild kullanarak her türlü proje oluşturuyorsanız, derleme hakkında bilgi kaydetmek için bir günlük dosyası oluşturabilirsiniz. Daha fazla bilgi için bkz. [Derleme günlüklerini alma](../msbuild/obtaining-build-logs-with-msbuild.md).

## <a name="to-view-the-build-log-file-for-a-c-project"></a>Bir C++ projesi için derleme günlük dosyasını görüntülemek için

1. **Windows Gezgini** veya **Dosya Gezgini**'nde, aşağıdaki dosyayı açın (proje kök klasörüne göre): *yayın* \\ <ProjectName> \> . Günlük * veya *hata ayıklama \\<ProjectName \> . log*

## <a name="to-create-a-build-log-file-for-a-managed-code-project"></a>Yönetilen kod projesi için bir yapı günlük dosyası oluşturmak için

1. Menü **çubuğunda Build**  >  **Build Solution** öğesini seçin.

2. **Çıkış** penceresinde, metinde herhangi bir yere tıklayın.

3. **CTRL** + **S** tuşuna basın.

   Visual Studio, derleme çıktısının kaydedileceği bir konum ister.

Ayrıca, `-fileLogger` ( `-fl` ) komut satırı seçeneğini kullanarak doğrudan komut satırından MSBuild 'i çalıştırarak da Günlükler oluşturabilirsiniz. Bkz. [MSBuild ile derleme günlükleri alma](../msbuild/obtaining-build-logs-with-msbuild.md).

## <a name="to-change-the-amount-of-information-included-in-the-build-log"></a>Yapı günlüğünde bulunan bilgi miktarını değiştirmek için

1. Menü çubuğunda **Araçlar**  >  **Seçenekler**' i seçin.

2. **Projeler ve çözümler** sayfasında, **derleme ve çalıştırma** sayfasını seçin.

3. **MSBuild proje derleme çıkışı ayrıntı** listesinde, aşağıdaki değerlerden birini seçin ve ardından **Tamam** düğmesini seçin.

    |Ayrıntı düzeyi|Description|
    | - |-----------------|
    |**Sess**|Yalnızca yapı özetini görüntüler.|
    |**En az**|Derleme ve hataların, uyarıların ve son derece önemli olarak sınıflandırılan mesajların özetini görüntüler.|
    |**Olağan**|Derleme özetini görüntüler; yüksek oranda önemli olarak sınıflandırılan hatalar, uyarılar ve iletiler ve yapı ana adımları. En sık bu ayrıntı düzeyini kullanacaksınız.|
    |**Ayrıntılı**|Derleme özetini görüntüler; yüksek oranda önemli olarak sınıflandırılan hatalar, uyarılar ve iletiler Tüm Yapı adımları; ve normal önem derecesine göre sınıflandırılan mesajlar.|
    |**Tanılama**|Yapı için kullanılabilen tüm verileri görüntüler. Özel derleme betiklerine ve diğer yapı sorunlarıyla ilgili sorunları ayıklamanıza yardımcı olması için bu ayrıntı düzeyini kullanabilirsiniz.|

     Daha fazla bilgi için bkz. [Seçenekler iletişim kutusu, projeler ve çözümler, oluşturma ve çalıştırma](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md) <xref:Microsoft.Build.Framework.LoggerVerbosity> .

    > [!IMPORTANT]
    > Değişikliklerinizin **Çıkış** penceresinde (tüm projeler) ve *\<ProjectName> . txt* dosyasında (yalnızca C++ projeleri) etkili olması için projeyi yeniden oluşturmanız gerekir.

## <a name="use-binary-logs-to-make-it-easier-to-browse-large-log-files"></a>Büyük günlük dosyalarına gözatmaya daha kolay hale getirmek için ikili günlükleri kullanın

İkili Günlükler, büyük günlüklerde bilgi bulmayı kolaylaştıran daha zengin bir günlük tarama deneyimine sahip olmanızı sağlayan, .NET projeleri için isteğe bağlı bir özelliktir. İkili günlükleri kullanmak için, [Proje sistemi araçları](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.ProjectSystemTools)'nı yükler. Daha fazla bilgi için bkz. [https://msbuildlog.com](https://msbuildlog.com) ve [ikili günlük](https://github.com/microsoft/msbuild/blob/master/documentation/wiki/Binary-Log.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da projeler ve çözümler oluşturma ve Temizleme](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Derleme ve oluşturma](../ide/compiling-and-building-in-visual-studio.md)
