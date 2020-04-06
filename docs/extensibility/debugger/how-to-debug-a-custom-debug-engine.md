---
title: 'Nasıl Yapılsın: Özel Hata Ayıklama Motoru | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, debugging
- debugging [Debugging SDK], custom debug engines
ms.assetid: df27a8d6-3938-45ff-b47f-b684e80b38a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c79790bfc9c9cd3767a453258b8c2d340f64d029
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738579"
---
# <a name="how-to-debug-a-custom-debug-engine"></a>Nasıl Yapılsın: Özel hata ayıklama altyapısı hata ayıklama
Proje türü, hata ayıklama altyapısını <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> (DE) yöntemden başlatır. Bu, DE'nin proje türünü [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] denetleme örneğinin denetimi altında başlatıldığı anlamına gelir. Ancak, bu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] örnek DE hata ayıklamak olamaz. Aşağıda, özel DE hata ayıklama sağlayan adımlar dır.

> [!NOTE]
> : "Özel hata ayıklama motoru" yordamında, eklemeden önce DE'nin başlamasını beklemeniz gerekir. DE başlatıldığında görünen DE'nizin başına bir ileti kutusu yerseniz, bu noktada ekleyebilir ve devam etmek için ileti kutusunu temizleyebilirsiniz. Bu şekilde, tüm DE olaylarını yakalayabilirsiniz.

> [!WARNING]
> Aşağıdaki yordamları denemeden önce uzaktan hata ayıklama yüklü olması gerekir. Ayrıntılar için [Uzaktan hata ayıklama](../../debugger/remote-debugging.md) bölümüne bakın.

## <a name="debug-a-custom-debug-engine"></a>Özel hata ayıklama altyapısı hata ayıklama

1. *Msvsmon.exe,* Uzaktan Hata Ayıklama Monitörü'ne başlayın.

2. *msvsmon.exe'deki* **Araçlar** menüsünden Seçenekler iletişim kutusunu açmak için **Seçenekler'i** seçin. **Options**

3. "Kimlik doğrulama yok" seçeneğini belirleyin ve **Tamam'ı**tıklatın.

4. Bir örneğini [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] başlatın ve özel DE projenizi açın.

5. İkinci bir örneğini başlatın [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ve DE'yi başlatan özel projenizi açın (geliştirme için, bu genellikle VSIP yüklendiğinde ayarlanan deneysel kayıt defteri kovanındadır).

6. Bu ikinci [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]durumda, özel projenizden bir kaynak dosya yükleyin ve programı debugged olarak başlatın. DE'nin yüklenmesine izin vermek için birkaç dakika bekleyin veya kesme noktası vurulana kadar bekleyin.

7. İlk örnekte [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (DE projenizle), **Hata Ayıklama** menüsünden **İşleme Ekle'yi** seçin.

8. **İşleme Ekle** iletişim kutusunda, **Aktarım'ı** **Uzak 'a (yalnızca kimlik doğrulaması olmadan yerel olarak)** değiştirin.

9. **Elemeyi** makinenizin adıyla değiştirin (not: girişlerin geçmişi vardır, bu nedenle bu adı yalnızca bir kez yazmanız gerekir).

10. Kullanılabilir **İşlemler** listesinde, çalışan DE'nizin örneğini seçin ve **Ekle** düğmesini tıklatın.

11. Semboller DE'nize yüklendikten sonra, DE kodunuza kesme noktaları yerleştirin.

12. Hata ayıklama işlemini her durdurup yeniden başlattığınızda, 6'dan 10'a kadar olan adımları yineleyin.

## <a name="debug-a-custom-project-type"></a>Özel proje türünü hata ayıklama

1. Normal [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kayıt kovanına başlayın ve proje tipi projenizi yükleyin (bu, proje türünüzdeki kaynağıdeğil, proje türünüzdeki bir anlık lamadır).

2. Proje özelliklerini açın ve **Hata Ayıklama** sayfasına gidin. **Komut**için, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE yolunu yazın (varsayılan olarak, bu *[sürücü]* \Program Files\Microsoft [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 8\Common7\IDE\devenv.exe olduğunu).

3. Komut **Bağımsız Değişkenleri**için, deneysel kayıt defteri kovanı için yazın `/rootsuffix exp` (VSIP kurulduğunda oluşturuldu).

4. Değişiklikleri kabul etmek için **Tamam** 'ı tıklayın.

5. **F5**tuşuna basarak proje türünü başlatın. Bu ikinci bir örneği [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]başlattı.

6. Bu noktada, proje türü kaynak kodunuza kesme noktaları yerleştirebilirsiniz.

7. İkinci [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]durumda, proje türünün yeni bir örneğini yükleyin veya oluşturun. Yükleme veya oluşturma sırasında kesme noktalarınız vurulabilir.

8. Proje türünü hata ayıklama.

9. Bir DE başlatma işlemini hata ayıklamayı seçerseniz, başlatıldıktan sonra DE'nize eklemek üzere "Özel hata ayıklama altyapısı hata ayıklama" yordamındaki adımları gerçekleştirebilirsiniz. Bu size üç [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] çalıştırma örneği verir: biri proje türü kaynağınız için, ikincisi anlık proje türünüz için ve üçüncüsü de'nize bağlı.

## <a name="see-also"></a>Ayrıca bkz.
- [Özel hata ayıklama altyapısı oluşturma](../../extensibility/debugger/creating-a-custom-debug-engine.md)
