---
title: Yapılandırma seçeneklerine genel bakış | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project configurations
- configuration options, about configuration options
ms.assetid: f4ad4dd3-b39e-42df-ad89-d403cdf24a2b
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0b37d93adbd2accb7a12fb176ab15aafc6914190
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64790938"
---
# <a name="configuration-options-overview"></a>Yapılandırma Seçeneklerine Genel Bakış
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

İçindeki projeler [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , derlenen, hata ayıklaması yapılan, çalıştırılan ve/veya dağıtılan birden fazla yapılandırmayı destekleyebilir. Yapılandırma, genellikle derleyici anahtarları ve dosya konumları gibi adlandırılmış özellikler kümesiyle tanımlanan bir yapı türüdür. Varsayılan olarak, yeni çözümler iki yapılandırma, hata ayıklama ve yayın içerir. Bu yapılandırma, varsayılan ayarları kullanılarak uygulanabilir veya özel çözümünüzü ve/veya proje gereksinimlerinizi karşılayacak şekilde değiştirilebilir. Bazı paketler iki şekilde oluşturulabilir: ActiveX Düzenleyicisi veya yerinde bileşen olarak. Ancak projelerin birden çok yapılandırmayı desteklemesi gerekmez. Yalnızca bir yapılandırma varsa, bu yapılandırma tüm çözüm yapılandırmalarına eşlenir.  
  
 Yapılandırmalar genellikle iki bölümden oluşur — yapılandırma adı (örneğin, hata ayıklama veya sürüm) ve platform ayarları. Yapılandırmanın platform adı, API kümesi veya işletim sistemi platformu gibi yapılandırmanın hedeflediği ortamı tanımlar. Kullanıcıları [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] bir platform oluşturamaz; bir proje VSPackage izin verdiği seçimlerde seçim yapmanız gerekir. Bir Kullanıcı VSPackage yüklediğinde, paketin geliştirilmesi sırasında oluşturulan dağıtım platformu, paket Oluşturucu tarafından ayarlanan ölçütlere göre istenen platform adlarını de açabilir. Kullanıcı daha sonra özellik sayfaları örnekleniken VSPackage aracılığıyla kullanılabilir hale getirilen platformlar listesinden seçim yapabilir.  
  
 Tüm projeler platformların kavramını desteklemediğinden, platform adları isteğe bağlıdır. Bir yapılandırma platform adı olmadığında, Kullanıcı arabiriminde "N/A" dizesi görüntülenir.  
  
 Her çözümün kendi yapılandırma kümesi vardır, tek seferde yalnızca biri etkin olabilir. Çözüm yapılandırması, her projeden birden fazla yapılandırma değildir. "Şundan fazla bilgi yok" seçeneği, bir projeyi çözüm yapılandırmasından hariç tutma seçeneği nedeniyle yapılır. Kullanıcılar kendi özel çözüm yapılandırmalarının oluşturulmasını sağlayabilir.  
  
 Aşağıdaki tabloda bir proje için tipik yapılandırma ayarları gösterilmektedir. Satırlar yapılandırma adlarıyla ve platform adları olan sütunlarla etiketlenir.  
  
|Yapılandırma adı|Platform — Win32|Platform — Win64|  
|------------------------|----------------------|----------------------|  
|Hata ayıklama|\<Debug Win32 settings>|\<Debug Win64 settings>|  
|Yayınla|\<Release Win32 settings>|\<Release Win64 settings>|  
|MyConfig|Yok|\<MyConfig Win64 settings>|  
  
> [!NOTE]
> Hedeflenmediğiniz proje Win32 'yi desteklemiyorsa "Win32" platformunu dışlayan bir "MyConfig" çözüm yapılandırması oluşturamazsınız.  
  
 Bir çözüm için etkin yapılandırmanın değiştirilmesi, bu çözümde oluşturulan, çalıştırılan, hata ayıklanan veya dağıtılan proje yapılandırmaları kümesini seçer. Örneğin, etkin çözüm yapılandırmasını yayından hata ayıklama olarak değiştirirseniz, bu Çözümdeki tüm projeler, çözümün hata ayıklama yapılandırmasında belirtilen proje yapılandırmasıyla otomatik olarak oluşturulur. Projenin yapılandırması, Kullanıcı ortamın Configuration Manager el ile değişiklikler yapmadığı takdirde hata ayıkla olarak da adlandırılır.  
  
 Her proje için depolanan çözüm yapılandırma özellikleri proje adı, proje yapılandırma adı, bayrak oluşturulup oluşturulmayacağını veya dağıtılacağını ve platform adının ne olduğunu belirten bayrakları içerir. Daha fazla bilgi için bkz. [çözüm yapılandırması](../../extensibility/internals/solution-configuration.md).  
  
 Kullanıcı, hiyerarşide çözümü seçerek (Çözüm Gezgini) ve özellik sayfalarını açarak çözüm yapılandırma parametrelerini görüntüleyebilir ve ayarlayabilir. Benzer şekilde, proje yapılandırma parametrelerini, Çözüm Gezgini bir proje seçerek ve bu projenin özellik sayfalarını açarak görüntüleyebilir ve ayarlayabilirsiniz.  
  
 Kullanıcı aynı zamanda yayın yapılandırma ayarlarını ve gerekirse hata ayıklama yapılandırma ayarlarıyla tüm rest 'yi kullanarak bir proje oluşturabilir. Daha fazla bilgi için bkz. [derleme Için proje yapılandırması](../../extensibility/internals/project-configuration-for-building.md).  
  
 Aşağıdaki diyagramda çözümü ve proje yapılandırmasını destekleyen arabirimlerin nasıl uygulandığı gösterilmektedir:  
  
 ![Yapılandırma arabirimleri grafiği](../../extensibility/internals/media/vsconfiginterfaces.gif "Vsconfigınterfaces")  
Yapılandırma arabirimleri  
  
 Önceki diyagramla ilgili birkaç Not:  
  
- `IDispatch` Yapılandırma nesnesinde isteğe bağlı olarak işaretlenir. Özellikle, tarama nesnesi üzerinde yapılandırma arabirimlerini sağlamak isteğe bağlıdır.  
  
- `IVsDebuggableProjectCfg` Yapılandırma nesnesinde isteğe bağlı olarak işaretlenir, ancak hata ayıklama desteği için gereklidir.  
  
- `IVsProjectCfg2` Yapılandırma nesnesinde isteğe bağlı olarak işaretlenir, ancak çıkış gruplama desteği için gereklidir.  
  
- `Config Provider`Nesne, isteğe bağlı bir nesne olarak işaretlenir, ancak bunu uygulamak için bir seçenek vardır. Nesneyi proje nesnesi üzerinde veya ayrı bir nesne üzerinde uygulayabilirsiniz.  
  
- `IVsCfgProvider2` Platform desteği ve yapılandırma düzenlemesi için gereklidir. `IVsCfgProvider` Bu işlevi uygulamadıysanız yeterlidir.  
  
- Diyagramda ayrı nesneler olarak gösterilen bu nesnelerden bazıları, özel tasarım gereksinimlerinize göre pratik olarak aynı sınıfta birleştirilebilir. Ancak, bu bölümün diğer konularında, bu nesnelerle ilişkili nesneler ve arabirimler diyagramda sunulan senaryoya göre ele alınacaktır.  
  
- Belirli nesneler ayrı ayrı uygulanır. Örneğin, proje ve çözüm oluşturma ayrı iş parçacıklarında ve derlemeyi yöneten nesne, derleme yapılandırmasını açıklayan nesneden ayrı olarak gerçekleşir.  
  
  Önceki diyagramda yapılandırma nesnesi arabirimleri ve yapılandırma sağlayıcısı nesne arabirimleri hakkında daha fazla bilgi için bkz. [Proje yapılandırma nesnesi](../../extensibility/internals/project-configuration-object.md). Ayrıca, derleme [Için proje yapılandırması](../../extensibility/internals/project-configuration-for-building.md) , Configuration Builder ve derleme bağımlılığı nesne arabirimleri hakkında daha fazla bilgi sağlar ve [dağıtımı yönetmeye yönelik proje yapılandırması](../../extensibility/internals/project-configuration-for-managing-deployment.md) , yapılandırma dağıtıcı ve dağıtım bağımlılığı nesnelerine eklenen arabirimleri daha da açıklar. Son olarak, çıkış [Için proje yapılandırması](../../extensibility/internals/project-configuration-for-output.md) çıktı grubunu ve çıkış nesnesi arabirimlerini ve yapılandırma bağımlı özellikleri görüntülemek ve ayarlamak için özellik sayfalarının kullanımını açıklar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>   
 [Derleme için proje yapılandırması](../../extensibility/internals/project-configuration-for-building.md)   
 [Çözüm Yapılandırması](../../extensibility/internals/solution-configuration.md)
