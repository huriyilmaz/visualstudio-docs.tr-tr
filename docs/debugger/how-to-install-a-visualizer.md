---
title: Görselleştirici yükleme | Microsoft Docs
description: Görselleştiriciyi yük devrede hata ayıklama kullanımı için kullanılabilir olacak şekilde Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 07/02/2021
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, visualizers
- visualizers, installing
ms.assetid: 3310ef43-515c-4d97-b0f9-51047247d3da
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 06ead535299bc0748489462a9c3adc04d045c08b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122128305"
---
# <a name="how-to-install-a-visualizer"></a>Nasıl Yapılır: Görselleştiriciyi Yükleme
Görselleştiriciyi oluşturduktan sonra, içinde kullanılabilir olması için görselleştiriciyi yüklemeniz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] gerekir. Görselleştirici yüklemek basit bir işlemdir.

> [!NOTE]
> UWP uygulamaları için yalnızca standart metin, HTML, XML ve JSON görselleştiricileri de kullanılabilir. Özel (kullanıcı tarafından oluşturulan) görselleştiriciler desteklenmiyor.

::: moniker range=">=vs-2019"
### <a name="to-install-a-visualizer-for-visual-studio-2019"></a>Visual Studio 2019 için görselleştirici yüklemek için

1. Yerleşik görselleştiriciyi içeren DLL'yi bulun.

   Genellikle, hem hata ayıklayıcı tarafı DLL hem de hata ayıklayıcı tarafı DLL'nin hedef platform olarak Herhangi **bir CPU** belirtmesi en iyisidir. Hata ayıklayıcı tarafı DLL Herhangi bir **CPU veya** **32 bit olması gerekir.** Hata ayıklama tarafı DLL'leri için hedef platform, hata ayıklama sürecine karşılık gelen bir platformdur.

   >[!NOTE]
   > Hata ayıklayıcı tarafı görselleştirici, Visual Studio yüklenir, bu nedenle bir dll .NET Framework gerekir. Hata ayıklayıcı tarafı, hata ayıklama .NET Framework hangi .NET Standard hata ayıklamaya bağlı olarak hata ayıklama veya Visual Studio.

2. Hata [ayıklayıcı tarafı](create-custom-visualizers-of-data.md#to-create-the-debugger-side) DLL'lerini (ve buna bağlı olduğu DLL'leri) aşağıdaki konumlardan herhangi birini kopyalayın:

    - *VisualStudioInstallPath*`\Common7\Packages\Debugger\Visualizers`

    - `My Documents\`*VisualStudioVersion*`\Visualizers`

3. Hata [ayıklayıcısı tarafındaki](create-custom-visualizers-of-data.md#to-create-the-visualizer-object-source-for-the-debuggee-side) DLL dosyasını aşağıdaki konumlardan birini kopyalayın:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers\` *Çerçeve*

    - `My Documents\`*VisualStudioVersion* `\Visualizers\` *Çerçeve*

    Burada *Framework şu* ikidir:
    - `net2.0` çalışma zamanı çalıştıran hata ayıkları `.NET Framework` için.
    - `netstandard2.0` destekleyen bir çalışma zamanı kullanan hata ayıkları için `netstandard 2.0` ( `.NET Framework v4.6.1+` veya `.NET Core 2.0+` ).
    - `netcoreapp` çalışma zamanı çalıştıran hata ayıkları `.NET Core` için. `.NET Core 2.0+`(destekler)

   Tek başına görselleştirici oluşturmak için hata ayıklama tarafı DLL gereklidir. Bu DLL, veri nesnesi için yöntemlerini uygulayan kodu <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> içerir.

   Hata ayıklama tarafı kodunu çoklu olarak hedefleyemiyorsanız, en az desteklenen TFM için hata ayıklayıcı tarafı DLL klasörüne yerleştirilsin.

4. Hata ayıklama oturumunu yeniden başlatın.

> [!NOTE]
> Yordam, 2017 ve Visual Studio farklıdır. Bu [makalenin önceki](how-to-install-a-visualizer.md?view=vs-2017&preserve-view=true) sürümüne bakın.
::: moniker-end

::: moniker range="vs-2017"
### <a name="to-install-a-visualizer-for-visual-studio-2017-and-older"></a>Visual Studio 2017 ve üzeri için görselleştirici yüklemek için

> [!IMPORTANT]
> Yalnızca .NET Framework görselleştiriciler 2017 Visual Studio daha eski bir modelde de desteklendi.

1. Yerleşik görselleştiriciyi içeren DLL'yi bulun.

2. DLL dosyasını aşağıdaki konumlardan herhangi bir konuma kopyalayın:

    - *VisualStudioInstallPath*`\Common7\Packages\Debugger\Visualizers`

    - `My Documents\`*VisualStudioVersion*`\Visualizers`

3. Hata ayıklama oturumunu yeniden başlatın.

> [!NOTE]
> Uzaktan hata ayıklama için yönetilen görselleştirici kullanmak için DLL'yi uzak bilgisayardaki aynı yola kopyalayın.
::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.
- [Özel Görselleştirici Oluşturma](../debugger/create-custom-visualizers-of-data.md)
- [Nasıl Yapılır: Görselleştirici Yazma](create-custom-visualizers-of-data.md)
