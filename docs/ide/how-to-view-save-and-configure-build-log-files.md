---
title: Nasıl yapı günlüğü dosyaları görüntüleme, kaydetme ve yapılandırma | Microsoft Docs
description: Derleme günlüğü dosyalarını görüntülemeyi, kaydetmeyi ve yapılandırmayı öğrenin. Bu dosyalar, derleme hatasıyla ilgili sorunları giderme gibi görevler için yararlı bilgiler sağlar.
ms.custom: SEO-VS-2020
ms.date: 08/28/2019
ms.technology: vs-ide-compile
ms.topic: how-to
ms.assetid: 75d38b76-26d6-4f43-bbe7-cbacd7cc81e7
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3316bf26f660b04c4f003b02523be3f9c408e73f
ms.sourcegitcommit: 42aec4a2ea6dec67dbe4c93bcf0fa1116a4b93d9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2021
ms.locfileid: "122980936"
---
# <a name="how-to-view-save-and-configure-build-log-files"></a>Nasıl kullanılır: Derleme günlüğü dosyalarını görüntüleme, kaydetme ve yapılandırma

IDE'de bir proje Visual Studio, bu derlemeyle ilgili bilgileri Çıkış penceresinde **görüntüebilirsiniz.** Bu bilgileri kullanarak, örneğin bir derleme hatasının sorunlarını giderebilirsiniz.

- C++ projeleri için, bir proje oluşturulduğunda oluşturulan ve kaydedilen günlük dosyasında da aynı bilgileri görüntüebilirsiniz. 

- Yönetilen kod projeleri için derleme çıkış penceresine tıklar ve Ctrl S **tuşlarına** + **basabilirsiniz.** Visual Studio, Çıkış penceresindeki bilgileri bir günlük dosyasına **kaydetmenizi** istediğiniz konumu girmenizi istiyor.

Her derleme hakkında ne tür bilgileri görüntülemek istediğinizi belirtmek için IDE'leri de kullanabilirsiniz.

MSBuild kullanarak herhangi bir tür proje MSBuild, derlemeyle ilgili bilgileri kaydetmek için bir günlük dosyası oluşturabilirsiniz. Daha fazla bilgi için [bkz. Derleme günlüklerini alma.](../msbuild/obtaining-build-logs-with-msbuild.md)

## <a name="to-view-the-build-log-file-for-a-c-project"></a>C++ projesinin derleme günlük dosyasını görüntülemek için

1. Windows **Gezgini'nde** **Dosya Gezgini** dosyasını açın (proje kök klasörüne göre):  \\ {ProjectName}. Log* veya *Debug \\ {ProjectName}.log*

## <a name="to-create-a-build-log-file-for-a-managed-code-project"></a>Yönetilen kod projesi için derleme günlüğü dosyası oluşturmak için

1. Menü çubuğunda Derleme   >  **Çözümü'ne tıklayın.**

2. Çıkış **penceresinde metinde** bir yere tıklayın.

3. **Ctrl** + **S tuşlarına basın.**

   Visual Studio çıkışını kaydetmek için bir konum girmenizi istiyor.

Ayrıca , () komut satırı MSBuild doğrudan komut satırı kullanarak `-fileLogger` `-fl` günlükler de çalıştırabilirsiniz. Bkz. [MSBuild ile derleme günlüklerini alma.](../msbuild/obtaining-build-logs-with-msbuild.md)

## <a name="to-change-the-amount-of-information-included-in-the-build-log"></a>Derleme günlüğüne dahil edilen bilgi miktarını değiştirmek için

1. Menü çubuğunda Araçlar **Seçenekleri'ne**  >  **tıklayın.**

2. Projeler **ve Çözümler sayfasında** Derleme ve **Çalıştırma sayfasını** seçin.

3. Proje **MSBuild çıkış ayrıntılılığı** listesinde aşağıdaki değerlerden birini seçin ve ardından Tamam **düğmesini** seçin.

    |Ayrıntılılık düzeyi|Description|
    | - |-----------------|
    |**Sessiz**|Yalnızca derlemenin özetini görüntüler.|
    |**En az**|Derlemenin özetini ve son derece önemli olarak sınıflandırılan hataların, uyarıların ve iletilerin özetini görüntüler.|
    |**Normal**|Derlemenin özetini görüntüler; son derece önemli olarak sınıflandırılan hatalar, uyarılar ve iletiler; ve derlemenin ana adımları. Bu ayrıntı düzeyini en sık kullanacağız.|
    |**Ayrıntılı**|Derlemenin özetini görüntüler; son derece önemli olarak sınıflandırılan hatalar, uyarılar ve iletiler; derlemenin tüm adımları; ve normal öneme sahip olarak kategorilere ayrılmış iletiler.|
    |**Tanılama**|Derleme için kullanılabilen tüm verileri görüntüler. Özel derleme betikleri ve diğer derleme sorunlarıyla ilgili sorunlarda hata ayıklamaya yardımcı olmak için bu ayrıntı düzeyini kullanabilirsiniz.|

     Daha fazla bilgi için [bkz. Seçenekler iletişim kutusu, Projeler ve Çözümler, Derleme ve Çalıştırma ve](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md) <xref:Microsoft.Build.Framework.LoggerVerbosity> .

    > [!IMPORTANT]
    > Değişikliklerinizin Çıkış penceresinde (tüm projeler)  ve.txt(yalnızca C++ projeleri) etkili olması *\<ProjectName> için* projeyi yeniden oluşturmanız gerekir.

## <a name="use-binary-logs-to-make-it-easier-to-browse-large-log-files"></a>Büyük günlük dosyalarına göz atmayı kolaylaştırmak için ikili günlükleri kullanma

İkili günlükler, .NET projeleri için büyük günlüklerde bilgi bulmanızı kolaylaştıracak daha zengin bir günlük tarama deneyimine sahip olmak için isteğe bağlı bir özelliktir. İkili günlükleri kullanmak için, Project [System Tools'larını yükleyin.](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.ProjectSystemTools) Daha fazla bilgi için [https://msbuildlog.com](https://msbuildlog.com) bkz. ve [İkili Günlük](https://github.com/microsoft/msbuild/blob/master/documentation/wiki/Binary-Log.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da proje ve çözüm oluşturma ve Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Derleme ve oluşturma](../ide/compiling-and-building-in-visual-studio.md)
