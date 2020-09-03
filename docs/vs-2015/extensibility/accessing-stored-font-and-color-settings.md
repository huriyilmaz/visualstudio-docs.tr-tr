---
title: Depolanan yazı tipine ve renk ayarlarına erişme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- fonts, accessing stored settings
- font and color control [Visual Studio SDK], persistence
- colors, accessing stored settings
ms.assetid: beba7174-e787-45c2-b6ff-a60f67ad4998
caps.latest.revision: 27
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fbb2f118d903eae2124e705f14c7aa7b51bf9c4d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67821838"
---
# <a name="accessing-stored-font-and-color-settings"></a>Depolanan Yazı Tipi ve Renk Ayarlarına Erişme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Tümleşik geliştirme ortamı (IDE), kayıt defterindeki yazı tipi ve renkler için değiştirilen ayarları depolar. <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>Bu ayarlara erişmek için arabirimi kullanabilirsiniz.  
  
## <a name="to-initiate-state-persistence-of-fonts-and-colors"></a>Yazı tiplerinin ve renklerin durum kalıcılığını başlatmak için  
 Yazı tipi ve renk bilgileri şu kayıt defteri konumundaki kategoriye göre saklanır: [HKCU\SOFTWARE\Microsoft \Adim \\ *\<Visual Studio version>* \Fontandcolors \\ *\<CategoryGUID>* ], burada *\<CategoryGUID>* Kategori GUID 'sidir.  
  
 Bu nedenle, kalıcılığı başlatmak için bir VSPackage şu şekilde olmalıdır:  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>Küresel hizmet sağlayıcısına çağrı yaparak bir arabirim elde edin `QueryService` .  
  
     `QueryService` öğesinin bir hizmet KIMLIĞI bağımsız değişkeni `SID_SVsFontAndColorStorage` ve ARABIRIM kimliği bağımsız değişkeni kullanılarak çağrılmalıdır `IID_IVsFontAndColorStorage` .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A>Bağımsız değişken olarak kategori GUID 'si ve mod bayrağını kullanarak kalıcı olacak bir kategoriyi açmak için yöntemini kullanın.  
  
  Bağımsız değişken tarafından belirtilen mod, `fFlags` <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> Numaralandırmadaki değerlerden oluşturulur. Bu mod denetimleri:  

  - Arabiriminden erişilebilen ayarlar <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> .  

  - Tüm ayarlar ya da yalnızca kullanıcıların, arabirim üzerinden alınabilir <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> .  

  - Değişiklikleri kullanıcı ayarlarına yayma şekli.  

  - Kullanılan renk değerlerinin biçimi.  

## <a name="to-use-state-persistence-of-fonts-and-colors"></a>Yazı tiplerinin ve renklerin durum kalıcılığını kullanmak için  
 Kalıcı yazı tipi ve renkler şunları içerir:  
  
- IDE ayarları, kayıt defterinde depolanan ayarlarla eşitleniyor.  
  
- Kayıt defteri değişiklik bilgileri yayılıyor.  
  
- Kayıt defterinde depolanan ayarları ayarlama ve alma.  
  
  Depolama ayarının IDE ayarlarıyla eşitlenmesi büyük ölçüde saydamdır. Temel IDE, **görüntüleme öğelerinin** güncelleştirilmiş ayarlarını otomatik olarak kategorilerin kayıt defteri girişlerine yazar.  
  
  Birden çok VSPackages belirli bir kategoriyi paylaşıyorsa, bir VSPackage, <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> depolanan kayıt defteri ayarlarını değiştirmek için arabirim yöntemleri kullanıldığında olayların oluşturulmasını gerektirir.  
  
  Varsayılan olarak, olay oluşturma etkin değildir. Olay oluşturmayı etkinleştirmek için bir kategorinin kullanılarak açılması gerekir <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> . Bu, IDE 'nin <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> VSPackage 'ın uyguladığı uygun yöntemi çağırmasını sağlar.  
  
> [!NOTE]
> **Yazı tipi ve renk** özelliği sayfasında yapılan değişiklikler, ' den bağımsız olaylar oluşturur <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>Sınıfının yöntemlerini çağırmadan önce önbelleğe alınmış yazı tipi ve renk ayarları güncelleştirmesinin gerekli olup olmadığını anlamak için arabirimini kullanabilirsiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> .  
  
### <a name="storing-and-retrieving-information"></a>Bilgileri depolama ve alma  
 Bir kullanıcının açık bir kategoride adlandırılmış bir görüntüleme öğesi için değiştirebileceği bilgileri almak veya yapılandırmak için VSPackages, <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetItem%2A> yöntemlerini çağırır.  
  
 Belirli bir kategorinin yazı tipi öznitelikleri hakkındaki bilgiler, ve yöntemleri kullanılarak elde <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> edilir <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetFont%2A> .  
  
> [!NOTE]
> `fFlags` <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> Bu kategori açıldığı zaman yöntemine geçirilen bağımsız değişken, <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> ve yöntemlerinin davranışını tanımlar <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> . Varsayılan olarak, bu yöntemler yalnızca değişmiş bir şekilde değişen bilgi aboutdisplay ıtemı döndürür. Ancak, bir kategori bayrağı kullanılarak açılırsa <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> , hem güncelleştirilmiş hem de değişmeyen görüntü öğelerine ve tarafından erişilebilir <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> .  
  
 Varsayılan olarak, yalnızca değiştirilen **görüntüleme öğeleri** bilgileri kayıt defterinde tutulur. <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>Arabirim, yazı tiplerinin ve renklerin tüm ayarlarını almak için kullanılamaz.  
  
> [!NOTE]
> <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A>Ve yöntemleri, <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> değişmeyen **görüntüleme öğeleri**hakkında bilgi almak için bunları kullandığınızda REGDB_E_KEYMISSING, (0x80040152l) döndürür.  
  
 Belirli bir **kategorideki** tüm **görüntüleme öğelerinin** ayarları, arabirimin yöntemleri kullanılarak elde edilebilir `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults` .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>   
 [Özel Kategoriler ve Görüntüleme Öğeleri Uygulama](../extensibility/implementing-custom-categories-and-display-items.md)
