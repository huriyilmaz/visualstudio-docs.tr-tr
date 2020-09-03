---
title: Yerel makinede Windows Mağazası uygulamalarını çalıştırın | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: e42a21a8-6423-4caf-b4dc-72b263e76019
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 031d764b95aa0f292702dde6167e0be9826270bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196306"
---
# <a name="run-windows-store-apps-on-the-local-machine"></a>Yerel makinede Microsoft Store uygulamaları çalıştırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yalnızca Windows için geçerlidir] (.. /Image/windows_only_content.png "windows_only_content")  
  
 Bir Windows Mağazası uygulamasında hata ayıklamak, test etmek veya performans analizini çalıştırmak için, uygulamayı Visual Studio 'Yu barındıran aynı makinede çalıştırabilirsiniz. Cihazdaki ekran dokunma etkin ise, uygulamanın tüm işlevlerini kullanabilirsiniz; Aksi takdirde, fare ve klavye hareketleri ile sınırlı olursunuz.  
  
## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> Bu konuda  
 Şunları öğrenebilirsiniz:  
  
 [Yerel makinede çalıştırma](#BKMK_How_to_run_on_a_local_machine)  
  
 [Tek bir monitörde Windows Mağazası uygulaması ve Visual Studio arasında geçiş yapma](#BKMK_How_to_switch_between_a_Windows_Store_app_and_Visual_Studio_on_a_single_monitor)  
  
## <a name="how-to-run-on-a-local-machine"></a><a name="BKMK_How_to_run_on_a_local_machine"></a> Yerel makinede çalıştırma  
 Uygulamayı yerel makinede çalıştırmak için hata ayıklayıcı **Standart** araç çubuğunda hata ayıklamayı Başlat düğmesinin yanındaki açılan listeden **yerel makine** ' yi seçin.  
  
 ![Yerel makinede Çalıştır](../debugger/media/vsrun-f5-local.png "VSRUN_F5_Local")  
  
 **Standart** araç çubuğunu göremiyorsanız, **Görünüm** menüsüne tıklayın, **araç çubukları**' nın üzerine gelin ve **Standart**' e tıklayın.  
  
 Açılan listede yaptığınız seçim proje özellikleri dosyasında kalıcıdır ve varsayılan çalıştırma hedefi olur.  
  
 Ayrıca, Çalıştır hedefini doğrudan proje özellikleri dosyasında da ayarlayabilirsiniz. **Çözüm Gezgini** ' de proje adına sağ tıklayın ve ardından **Özellikler**' i seçin. Ardından aşağıdakilerden birini yapın:  
  
- C# ve Visual Basic projelerinde, **Hata Ayıkla** ' ya tıklayın ve ardından **hedef cihaz** açılan listesinden **yerel makine** ' yi seçin.  
  
     ![C&#35; ve Visual Basic projesi Özellik sayfası](../debugger/media/vsrun-cs-vb-projprop-local.png "VSRUN_CS_VB_ProjProp_Local")  
  
- C++ ve JavaScript projelerinde, **yapılandırma özellikleri** düğümünü genişletin, **hata ayıklama**' ye tıklayın ve ardından **hata ayıklayıcıdan** **yerel hata ayıklayıcı** ' yı seçerek listeden başlatın.  
  
     ![C&#43;&#43; ve JavaScript proje özellikleri sayfası](../debugger/media/vsrun-cpp-js-projprop-local.png "VSRUN_CPP_JS_ProjProp_Local")  
  
## <a name="how-to-switch-between-a-windows-store-app-and-visual-studio-on-a-single-monitor"></a><a name="BKMK_How_to_switch_between_a_Windows_Store_app_and_Visual_Studio_on_a_single_monitor"></a> Tek bir monitörde Windows Mağazası uygulaması ve Visual Studio arasında geçiş yapma  
 **Windows Mağazası uygulamasının çalışan bir örneğinden Visual Studio 'ya geçiş yapmak için**  
  
 Bir Windows Mağazası uygulamasını yerel bir makinede çalıştırdığınızda ve yalnızca tek bir izleyici kullandığınızda uygulamayı çalışır durumda bırakarak Visual Studio 'ya geri dönmek isteyebilirsiniz. Örneğin, uygulama bir olay için bekleyen veya uzun veya sonsuz bir döngüde yakalanan bir kesme noktası tarafından erişilemeyen bir durumda olabilir. Visual Studio 'ya dönmek için ALT + TAB tuşlarına basın.
