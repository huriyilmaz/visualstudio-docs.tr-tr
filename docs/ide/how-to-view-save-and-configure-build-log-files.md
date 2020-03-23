---
title: Yapı günlüğü dosyalarını görüntüleme, kaydetme ve yapılandırma | Microsoft Dokümanlar
ms.date: 08/28/2019
ms.technology: vs-ide-compile
ms.topic: conceptual
ms.assetid: 75d38b76-26d6-4f43-bbe7-cbacd7cc81e7
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d3996ef0db25a6552a1a32cd121dbf2f750d460c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114471"
---
# <a name="how-to-view-save-and-configure-build-log-files"></a>Nasıl yapılsın: Yapı günlüğü dosyalarını görüntüleme, kaydetme ve yapılandırma

Visual Studio IDE'de bir proje yaptıktan sonra, **Çıktı** penceresinde bu yapıyla ilgili bilgileri görüntüleyebilirsiniz. Bu bilgileri kullanarak, örneğin, bir yapı hatagiderme olabilir. 

- C++ projeleri için, aynı bilgileri otomatik olarak oluşturulan ve kaydedilen *bir .txt* dosyasında da görüntüleyebilirsiniz. 

- Yönetilen kod projeleri için yapı çıktısı penceresinden tıklayıp **Ctrl**+**S**tuşuna basabilirsiniz. Visual Studio, **çıktı** penceresinden *.txt* dosyasına bilgileri kaydetmek için bir konum ister. 

IDE'yi, her yapı hakkında görüntülemek istediğiniz bilgileri belirtmek için de kullanabilirsiniz.

MSBuild'i kullanarak herhangi bir proje oluşturursanız, yapı yla ilgili bilgileri kaydetmek için bir *.txt* dosyası oluşturabilirsiniz. Daha fazla bilgi için [bkz.](../msbuild/obtaining-build-logs-with-msbuild.md)

## <a name="to-view-the-build-log-file-for-a-c-project"></a>C++ projesinin yapı günlüğü dosyasını görüntülemek için

1. Windows Explorer veya **File Explorer'da,** aşağıdaki dosyayı **Windows Explorer** açın: * \\...\Visual Studio \<Version\\ \>\>\\ \Projects\> \\<ProjectName<ProjectName\>\Debug<ProjectName .txt*

## <a name="to-create-a-build-log-file-for-a-managed-code-project"></a>Yönetilen kod projesi için yapı günlüğü dosyası oluşturmak için

1. Menü çubuğunda **Yapı** > **Çözüm'üne**bakın.

2. **Çıktı** penceresinde, metinde bir yere tıklayın.

3. **Ctrl**+**S**tuşuna basın.

   Visual Studio, yapı çıktısını kaydetmek için bir konum ister.

MSBuild'i doğrudan komut satırından çalıştırarak ( `-fileLogger` `-fl`) komut satırı seçeneğini kullanarak günlükler oluşturabilirsiniz. Bkz. [MSBuild ile yapı günlükleri edinin.](../msbuild/obtaining-build-logs-with-msbuild.md)

## <a name="to-change-the-amount-of-information-included-in-the-build-log"></a>Yapı günlüğüne dahil edilen bilgi miktarını değiştirmek için

1. Menü çubuğunda **Araç** > **Seçenekleri'ni**seçin.

2. Projeler **ve Çözümler** sayfasında **Yap ve Çalıştır** sayfasını seçin.

3. **MSBuild proje oluşturma çıktı ayrıntılı listesinde,** aşağıdaki değerlerden birini seçin ve sonra **Tamam** düğmesini seçin.

    |Ayrıntılı lık düzeyi|Açıklama|
    | - |-----------------|
    |**Sessiz**|Yalnızca yapının bir özetini görüntüler.|
    |**En az**|Yapının ve hataların, uyarıların ve son derece önemli olarak sınıflandırılan iletilerin bir özetini görüntüler.|
    |**Normal**|Yapının bir özetini görüntüler; hatalar, uyarılar ve son derece önemli olarak kategorize edilen iletiler; ve yapının ana adımları. Bu ayrıntı düzeyini en sık kullanırsınız.|
    |**Ayrıntılı**|Yapının bir özetini görüntüler; hatalar, uyarılar ve son derece önemli olarak kategorize edilen iletiler; yapının tüm adımları; ve normal öneme sahip olarak kategorize edilen iletiler.|
    |**Tanılama**|Yapı için kullanılabilen tüm verileri görüntüler. Özel yapı komut dosyaları ve diğer yapı sorunlarıyla ilgili hata ayıklama sorunlarına yardımcı olmak için bu ayrıntı düzeyini kullanabilirsiniz.|

     Daha fazla bilgi için seçenekler [iletişim kutusu, Projeler ve Çözümler, Oluştur ve Çalıştır](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md) ve <xref:Microsoft.Build.Framework.LoggerVerbosity>.

    > [!IMPORTANT]
    > Değişikliklerinizin **Çıktı** penceresinde (tüm projeler) ve * \<ProjectName>.txt* dosyasında (yalnızca C++ projeleri) etkili olması için projeyi yeniden oluşturmanız gerekir.

## <a name="use-binary-logs-to-make-it-easier-to-browse-large-log-files"></a>Büyük günlük dosyalarına göz atmayı kolaylaştırmak için ikili günlükleri kullanın

İkili günlükler, büyük günlüklerde bilgi bulmanızı kolaylaştırabilecek daha zengin bir günlük tarama deneyimine sahip olmak sağlayan .NET projeleri için isteğe bağlı bir özelliktir. İkili günlükleri kullanmak için [Proje Sistemi Araçlarını](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.ProjectSystemTools)yükleyin. Daha fazla bilgi [https://msbuildlog.com](https://msbuildlog.com) için bkz ve [İkili Günlük](https://github.com/microsoft/msbuild/blob/master/documentation/wiki/Binary-Log.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da projeler ve çözümler oluşturun ve temizleyin](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Derleme ve oluşturma](../ide/compiling-and-building-in-visual-studio.md)
