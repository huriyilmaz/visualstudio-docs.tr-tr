---
title: 'Nasıl yapılır: özel hata ayıklama altyapısında hata ayıklama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, debugging
- debugging [Debugging SDK], custom debug engines
ms.assetid: df27a8d6-3938-45ff-b47f-b684e80b38a0
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b7e710cec4536a5a1327580e56c60cb23ca36f4c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64797389"
---
# <a name="how-to-debug-a-custom-debug-engine"></a>Nasıl Yapılır: Özel Hata Ayıklama Altyapısında Hata Ayıklama
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Proje türü, yöntemi hata ayıklama altyapısını (DE) başlatır <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> . Bu, öğesinin proje türünü denetleme örneğinin denetimi altında başlatıldığı anlamına gelir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Ancak, bu örneği [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] de hata ayıklaması yapılamaz. Özel DE hata ayıklamanıza olanak tanımak için aşağıdaki adımlar aşağıda verilmiştir.  
  
> [!NOTE]
> : "Özel hata ayıklama altyapısında hata ayıklama" yordamında, ona iliştirebilmeniz için önce DE ' ın başlamasını beklemeniz gerekir. Aynı zamanda, ve ' ı başladığında görünen başlangıcına yakın bir ileti kutusu yerleştirirseniz, bu noktaya iliştirebilir ve sonra devam etmek için ileti kutusunu temizleyebilirsiniz. Böylece tüm olayları yakalayabilirsiniz.  
  
> [!WARNING]
> Aşağıdaki yordamları gerçekleştirmeden önce uzaktan hata ayıklamanın yüklü olması gerekir. Ayrıntılar için bkz. [Uzaktan hata ayıklama](../../debugger/remote-debugging.md) .  
  
### <a name="debugging-a-custom-debug-engine"></a>Özel hata ayıklama altyapısında hata ayıklama  
  
1. Uzaktan hata ayıklama Izleyicisi msvsmon.exe başlatın.  
  
2. msvsmon.exe **Araçlar** menüsünde **Seçenekler iletişim kutusunu** açmak için **Seçenekler** ' i seçin.  
  
3. "Kimlik doğrulaması yok" seçeneğini belirleyip **Tamam**' a tıklayın.  
  
4. Bir örneğini başlatın [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ve özel de projenizi açın.  
  
5. İkinci bir örneğini başlatın [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ve öğesini Başlatan özel projenizi açın (geliştirme için, bu genellikle VSIP yüklendiğinde ayarlanan Deneysel kayıt defteri kovanında bulunur).  
  
6. Bu ikinci örneğinde [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , özel projenizden bir kaynak dosyası yükleyin ve hata Ayıklanacak programı başlatın. Yükleme işleminin veya bir kesme noktasına gelene kadar beklemeniz için birkaç dakika bekleyin.  
  
7. İlk örneğinde [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (ve projem), **hata ayıklama** menüsünden **İşleme İliştir** ' i seçin.  
  
8. **Işleme İliştir** iletişim kutusunda, **aktarımı** **uzak (kimlik doğrulama olmadan yerel)** olarak değiştirin.  
  
9. **Niteleyiciyi** makinenizin adı olarak değiştirin (Note: giriş geçmişi var, bu nedenle bu adı yalnızca bir kez yazmanız gerekir).  
  
10. **Kullanılabilir süreçler** listesinde, çalıştıran uygulamanızın örneğini seçin ve **Ekle** düğmesine tıklayın.  
  
11. Semboller ' de yüklendikten sonra, kesme noktalarını DE kodunuzla yerleştirin.  
  
12. Hata ayıklama işlemini durdurup yeniden başlattığınızda, 6 ile 10 arasındaki adımları yineleyin.  
  
### <a name="debugging-a-custom-project-type"></a>Özel proje türünde hata ayıklama  
  
1. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Normal kayıt defteri kovanında başlatın ve proje türü projenizi (Bu, kaynak, proje türünün örneklenmesi değil, proje türüne) yükleyin.  
  
2. Proje özelliklerini açın ve **hata ayıklama** sayfasına gidin. **Komut**için, IDE yolunu yazın [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (varsayılan olarak bu *[sürücü]* \Program Files\Microsoft [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 8\Common7\IDE\devenv.exe).  
  
3. **Komut bağımsız değişkenleri**için, `/rootsuffix exp` Deneysel kayıt defteri kovanını (VSIP yüklendiğinde oluşturulur) yazın.  
  
4. Değişiklikleri kabul etmek için **Tamam** 'ı tıklayın.  
  
5. F5 tuşuna basarak proje türünü başlatın. Bu, ikinci bir örneğini başlatacaktır [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
6. Bu noktada, kesme noktalarını proje türü kaynak kodunuza yerleştirebilirsiniz.  
  
7. İkinci örneğinde [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , proje türünün yeni bir örneğini yükleyin veya oluşturun. Yükleme veya oluşturma sırasında kesme noktalarınız isabet edebilir.  
  
8. Proje türünde hata ayıklayın.  
  
9. Bir DE başlatma işleminde hata ayıklamayı seçerseniz, "özel hata ayıklama altyapısında hata ayıklama" yordamında, başlatıldıktan sonra da eklemek için bu adımları uygulayabilirsiniz. Bu, size üç farklı örnek sağlar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] : proje türü kaynağınız için bir tane, örneklendirilmiş proje türü için ikinci bir, ve de üçüncü olarak eklenmiş.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özel Hata Ayıklama Altyapısı Oluşturma](../../extensibility/debugger/creating-a-custom-debug-engine.md)
