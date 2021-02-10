---
title: 'Nasıl yapılır: özel hata ayıklama altyapısında hata ayıklama | Microsoft Docs'
description: Özel hata ayıklama motorunda veya özel bir proje türünde hata ayıklamak için Visual Studio 'Yu kullanmanıza imkan tanıyan adımlar hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debug engines, debugging
- debugging [Debugging SDK], custom debug engines
ms.assetid: df27a8d6-3938-45ff-b47f-b684e80b38a0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 46e9b18f7bb34433ff86fe6a5bede436228d3ff1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947703"
---
# <a name="how-to-debug-a-custom-debug-engine"></a>Nasıl yapılır: özel hata ayıklama altyapısında hata ayıklama
Proje türü, yöntemi hata ayıklama altyapısını (DE) başlatır <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> . Bu, öğesinin proje türünü denetleme örneğinin denetimi altında başlatıldığı anlamına gelir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Ancak, bu örneği [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de hata ayıklaması yapılamaz. Özel DE hata ayıklamanıza olanak tanıyan adımlar aşağıda verilmiştir.

> [!NOTE]
> : "Özel hata ayıklama altyapısında hata ayıkla" yordamında, ona iliştirebilmeniz için önce DE ' ın başlamasını beklemeniz gerekir. Aynı zamanda, ve ' ı başladığında görünen başlangıcına yakın bir ileti kutusu yerleştirirseniz, bu noktaya iliştirebilir ve sonra devam etmek için ileti kutusunu temizleyebilirsiniz. Böylece tüm olayları yakalayabilirsiniz.

> [!WARNING]
> Aşağıdaki yordamları gerçekleştirmeden önce uzaktan hata ayıklamanın yüklü olması gerekir. Ayrıntılar için bkz. [Uzaktan hata ayıklama](../../debugger/remote-debugging.md) .

## <a name="debug-a-custom-debug-engine"></a>Özel hata ayıklama altyapısında hata ayıklama

1. Uzaktan hata ayıklama Izleyicisi *msvsmon.exe* başlatın.

2. *msvsmon.exe* **Araçlar** menüsünde **Seçenekler iletişim kutusunu** açmak için **Seçenekler** ' i seçin.

3. "Kimlik doğrulaması yok" seçeneğini belirleyip **Tamam**' a tıklayın.

4. Bir örneğini başlatın [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ve özel de projenizi açın.

5. İkinci bir örneğini başlatın [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ve öğesini Başlatan özel projenizi açın (geliştirme için, bu genellikle VSIP yüklendiğinde ayarlanan Deneysel kayıt defteri kovanında bulunur).

6. Bu ikinci örneğinde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , özel projenizden bir kaynak dosyası yükleyin ve hata Ayıklanacak programı başlatın. Yükleme işleminin veya bir kesme noktasına gelene kadar beklemeniz için birkaç dakika bekleyin.

7. İlk örneğinde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (ve projem), **hata ayıklama** menüsünden **İşleme İliştir** ' i seçin.

8. **Işleme İliştir** iletişim kutusunda, **aktarımı** **uzak (kimlik doğrulama olmadan yerel)** olarak değiştirin.

9. **Niteleyiciyi** makinenizin adı olarak değiştirin (Note: girişlerin bir geçmişi varsa, bu adı yalnızca bir kez yazmanız gerekir).

10. **Kullanılabilir süreçler** listesinde, çalıştıran uygulamanızın örneğini seçin ve **Ekle** düğmesine tıklayın.

11. Semboller ' de yüklendikten sonra, kesme noktalarını DE kodunuzla yerleştirin.

12. Hata ayıklama işlemini durdurup yeniden başlattığınızda, 6 ile 10 arasındaki adımları yineleyin.

## <a name="debug-a-custom-project-type"></a>Özel proje türünde hata ayıklama

1. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Normal kayıt defteri kovanında başlatın ve proje türü projenizi (Bu, kaynak, proje türünün örneklenmesi değil, proje türüne) yükleyin.

2. Proje özelliklerini açın ve **hata ayıklama** sayfasına gidin. **Komut** için, IDE yolunu yazın [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (varsayılan olarak bu *[sürücü]* \Program Files\Microsoft [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 8\Common7\IDE\devenv.exe).

3. **Komut bağımsız değişkenleri** için, `/rootsuffix exp` Deneysel kayıt defteri kovanını (VSIP yüklendiğinde oluşturulur) yazın.

4. Değişiklikleri kabul etmek için **Tamam** 'ı tıklayın.

5. **F5** tuşuna basarak proje türünü başlatın. Bu, ikinci bir örneğini başlatır [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

6. Bu noktada, kesme noktalarını proje türü kaynak kodunuza yerleştirebilirsiniz.

7. İkinci örneğinde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , proje türünün yeni bir örneğini yükleyin veya oluşturun. Yükleme veya oluşturma sırasında kesme noktalarınız isabet edebilir.

8. Proje türünde hata ayıklayın.

9. Bir DE başlatma işleminde hata ayıklamayı seçerseniz, "özel hata ayıklama altyapısında hata ayıkla" yordamında, başlatıldıktan sonra da eklemek için bu adımları uygulayabilirsiniz. Bu, size üç farklı örnek sağlar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] : proje türü kaynağınız için bir tane, örneklendirilmiş proje türü için ikinci bir, ve de üçüncü olarak eklenmiş.

## <a name="see-also"></a>Ayrıca bkz.
- [Özel hata ayıklama altyapısı oluşturma](../../extensibility/debugger/creating-a-custom-debug-engine.md)
