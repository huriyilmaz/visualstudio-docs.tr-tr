---
title: Eski Iş akışlarında hata ayıklama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, debugging
- debugging, workflows
- debugging workflows
ms.assetid: e6097b47-760a-4b30-a92c-ae70cdbda49f
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 40ae0a08e1623e1b90046d164d8bfe04eaf67229
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656863"
---
# <a name="debugging-legacy-workflows"></a>Eski İş Akışlarında Hata Ayıklama
[!INCLUDE[wfd1](../includes/wfd1-md.md)] [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] [!INCLUDE[wf](../includes/wf-md.md)] Target.NET Framework 3,0 veya 3,5 çalıştıran uygulamalar oluşturmak için eski sürümü kullanıyorsanız, kesme noktaları ayarlayarak, işlemlere ekleyerek ve iş parçacıklarını ve çağrı yığınını inceleyerek diğer programlar gibi iş akışlarınızda hata ayıklaması yapabilirsiniz. Uzaktan hata ayıklama seçeneğiniz de vardır.

> [!NOTE]
> Makinenizde birden fazla Visual Studio sürümü yüklenip kaldırılırsa, WF3 hata ayıklaması aşağıdaki iki olasılıktan biriyle başarısız olabilir:
>
> - Kesme noktalarınız isabet etmez.
>   - Aşağıdaki ileti görüntülenir:
>
>   **Web sunucusunda hata ayıklama başlatılamıyor. Hata ayıklayıcı düzgün yüklenmemiş.  İstenen kod türünde hata ayıklaması yapılamıyor.  Hata ayıklayıcıyı yüklemek veya onarmak için kurulumu çalıştırın.**
>
>   3,0 veya 3,5 iş akışlarının hata .NET Framework ayıklaması sırasında bu senaryolardan herhangi biri oluşursa, Visual Studio yüklemesinde bir onarım gerçekleştirin.

 [!INCLUDE[wf2](../includes/wf2-md.md)] Aşağıdaki standart [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] hata ayıklama pencereleri ile tümleşir:

- **Kesme noktası**: beklendiği gibi çalışır, ancak işlev adı için bir etkinlik belirtirsiniz.

- **Çağrı yığını**: bir iş akışı örneğinde yürütülen etkinliklerin anahattını sağlamak için değiştirilir. **Çağrı yığını** penceresindeki girişler, çalışan etkinliklerin derinlemesine bir ilk aramasından oluşur. Odağı Seçili etkinliğe yerleştirmek için bir girişe çift tıklayabilirsiniz.

- **Iş parçacıkları**: hata ayıklanan iş akışı ÖRNEĞININ örnek kimliğini sağlar.

  Windows Workflow Foundation için Visual Studio aşağıdaki hata ayıklama özelliklerini desteklemez:

- Tasarımcı yüzeyinde koşullu kesme noktaları.

- QuickWatch.

- Sonraki ifadeyi ayarla.

- İmlece kadar Çalıştır.

- Düzenle ve devam et.

- Tam zamanında hata ayıklama.

- Karışık modda hata ayıklama.

## <a name="in-this-section"></a>Bu Bölümde
 [Windows Workflow Foundation için Visual Studio Hata Ayıklayıcısını Çağırma (Eski)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)

 [Windows Workflow Foundation için Visual Studio Hata Ayıklayıcısını Devre Dışı Bırakma (Eski)](../workflow-designer/disabling-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)

 [Nasıl Yapılır: ASP.NET Tabanlı İş Akışlarında Hata Ayıklama (Eski)](../workflow-designer/how-to-debug-aspnet-based-workflows-legacy.md)

 [Nasıl Yapılır: İş Akışlarında Kesme Noktası Ayarlama (Eski)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)

 [Uzak Bir Bilgisayardan İş Akışlarında Hata Ayıklama (Eski)](../workflow-designer/debugging-workflows-from-a-remote-computer-legacy.md)

 [Hata Ayıklama Adımlama Seçenekleri (Eski)](../workflow-designer/debug-stepping-options-legacy.md)

 [Nasıl Yapılır: Hata Ayıklama Adımlama Seçeneğini Değiştirme (Eski)](../workflow-designer/how-to-change-the-debug-stepping-option-legacy.md)