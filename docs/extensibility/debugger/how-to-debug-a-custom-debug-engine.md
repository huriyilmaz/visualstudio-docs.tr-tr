---
title: 'Nasıl: Özel Hata Ayıklama Altyapısı hata ayıklama | Microsoft Docs'
description: Özel hata ayıklama altyapınız veya özel bir proje Visual Studio hata ayıklamak için Visual Studio adımlarını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debug engines, debugging
- debugging [Debugging SDK], custom debug engines
ms.assetid: df27a8d6-3938-45ff-b47f-b684e80b38a0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: ecaa14f0b9576ab805aa0a880f82766f6fe546c4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122057882"
---
# <a name="how-to-debug-a-custom-debug-engine"></a>Nasıl 2: Özel hata ayıklama altyapısında hata ayıklama
Proje türü, yönteminden hata ayıklama altyapısını (DE) <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> başlatıyor. Bu, DE'nin proje türünü denetleme örneğinin denetimi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] altında başlat olduğu anlamına gelir. Ancak, bu örneği [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] DE'de hata ayıkamaz. Özel DE'nizin hata ayıklamasına olanak sağlayan adımlar şunlardır.

> [!NOTE]
> : "Özel hata ayıklama altyapısında hata ayıklama" yordamında, eklemeden önce DE'nin başlamayı beklemesi gerekir. DE başlatıldığında görünen DE'nizin başına bir ileti kutusu yer alırsanız, bu noktaya iliştirin ve devam etmek için ileti kutusunu temizleyin. Bu şekilde, tüm DE olaylarını yakalayabilirsiniz.

> [!WARNING]
> Aşağıdaki yordamları denemeden önce uzaktan hata ayıklama yüklü olması gerekir. Ayrıntılar [için bkz. Uzaktan](../../debugger/remote-debugging.md) hata ayıklama.

## <a name="debug-a-custom-debug-engine"></a>Özel hata ayıklama altyapısında hata ayıklama

1. Uzaktan *msvsmon.exe* İzleyicisi'ne 'den başlama.

2. *msvsmon.exe'daki Araçlar menüsünde* **Seçenekler'i** seçerek **Seçenekler iletişim** kutusunu açın. 

3. "Kimlik doğrulaması yok" seçeneğini belirleyin ve Tamam'a **tıklayın.**

4. bir örneği [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] başlatarak özel DE projenizi açın.

5. İkinci bir örneğini başlatıp DE'i başlatan özel projenizi açın (geliştirme için bu genellikle VSIP yüklenirken ayarlanmış deneysel kayıt defteri [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kovanının içindedir).

6. Bu ikinci [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] örneğinde, özel projenize bir kaynak dosyası yükleme ve hata ayıklama için programı başlatma. DE'nin yüklemesine izin vermek için birkaç dakika bekleyin veya bir kesme noktası gelene kadar bekleyin.

7. İlk örneğinde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (DE projeniz ile), Hata Ayıklama **menüsünden İşleme** **Ekle'yi** seçin.

8. İşleme Ekle **iletişim kutusunda,** Aktarım'ı Uzak (Yalnızca **kimlik** **doğrulamasız yerel) olarak değiştirebilirsiniz.**

9. **Niteleyiciyi** makinenizin adıyla (not: Giriş geçmişi vardır, bu nedenle bu adı yalnızca bir kez yazmanız gerekir) olarak değiştirebilirsiniz.

10. Kullanılabilir **İşlemler listesinde,** çalışan DE örneğinizi seçin ve Ekle **düğmesine** tıklayın.

11. DE'nize semboller yüklendikten sonra DE kodunuza kesme noktaları girin.

12. Hata ayıklama işlemini durduran ve sonra yeniden başlatan her zaman 6 ile 10. adımları tekrarlayın.

## <a name="debug-a-custom-project-type"></a>Özel proje türünde hata ayıklama

1. Normal kayıt defteri kovanını başlatarak proje türü projenizi (bu, proje türü örneğinizin değil, kaynağın proje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] türüne) yükleme.

2. Hata Project açın ve Hata Ayıklama **sayfasına** gidin. Komut **için,** IDE'nin yolunu yazın (varsayılan olarak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , *[sürücü]* \Program Files\Microsoft [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 8\Common7\IDE\devenv.exe).

3. Komut Bağımsız **Değişkenleri için** deneysel kayıt `/rootsuffix exp` defteri kovanı (VSIP yüklenirken oluşturulur) yazın.

4. Değişiklikleri kabul etmek için **Tamam** 'ı tıklayın.

5. F5 tuşuna basarak **proje türlerinizi başlatma.** Bu, ikinci bir örneğini [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] başlatıyor.

6. Bu noktada, proje türü kaynak kodunuz için kesme noktaları yer almaktadır.

7. İkinci [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] örneğinde, proje türüne yeni bir örnek yük veya oluşturun. Yükleme veya oluşturma sırasında kesme noktalarınıza isabet ediyor olabilir.

8. Proje türü hata ayıklama.

9. DE başlatma işleminin hata ayıklaması seçerseniz, "Özel hata ayıklama altyapısında hata ayıklama" yordamında yer alan adımları, başlatıldıktan sonra DE'nize eklemek üzere gerçekleştirebilirsiniz. Bu size üç çalıştırma örneği sağlar: biri proje türü kaynağınız için, ikincisi örneklenmiş proje türü için ve üçüncüsü [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] DE'nize bağlı.

## <a name="see-also"></a>Ayrıca bkz.
- [Özel hata ayıklama altyapısı oluşturma](../../extensibility/debugger/creating-a-custom-debug-engine.md)
