---
title: Yapılandırma Seçeneklerine Genel Bakış | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations
- configuration options, about configuration options
ms.assetid: f4ad4dd3-b39e-42df-ad89-d403cdf24a2b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6d5ac25fcef7b942b791402baf17982c9810e92a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709404"
---
# <a name="configuration-options-overview"></a>Yapılandırma seçeneklerine genel bakış
Projeler, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] oluşturulabilen, hata ayıklanabilen, çalıştırılabilen ve/veya dağıtılabilen birden çok yapılandırmayı destekleyebilir. Yapılandırma, adlandırılmış özellikler kümesi, genellikle derleyici anahtarları ve dosya konumları ile açıklanan bir yapı türüdür. Varsayılan olarak, yeni çözümler iki yapılandırmaları, *Hata Ayıklama* ve *Release*içerir. Bu yapılandırmalar varsayılan ayarları kullanılarak uygulanabilir veya özel çözüm ve/veya proje gereksinimlerinizi karşılayacak şekilde değiştirilebilir. Bazı paketler iki şekilde oluşturulabilir: ActiveX düzenleyicisi olarak veya yerinde bileşen olarak. Ancak, projelerin birden çok yapılandırmayı desteklemesi gerekmez. Yalnızca bir yapılandırma varsa, bu yapılandırma tüm çözüm yapılandırmalarına eşlenir.

 Yapılandırmalar genellikle iki bölümden oluşur: yapılandırma adı *(Hata Ayıklama* veya *Sürüm*gibi) ve platform ayarları. Yapılandırmanın platform adı, bir API kümesi veya işletim sistemi platformu gibi yapılandırmanın hedeflenedığı ortamı tanımlar. Kullanıcılar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bir platform oluşturamaz; vspackage projesinin izin verdiği seçimlerden birini seçmelidirler. Bir kullanıcı bir VSPackage yüklediğinde, paketin geliştirilmesi sırasında oluşturulan dağıtım platformu, paket oluşturucu tarafından belirlenen ölçütlere göre istenilen platform adını ortaya çıkarabilir. Kullanıcı daha sonra, özellik sayfaları anında kullanıma sunulduğunda VSPackage aracılığıyla sunulan platformlar listesinden seçim yapabilir.

 Tüm projeler platform kavramını desteklemediğinden platform adları isteğe bağlıdır. Bir yapılandırmada bir platform adı olmadığında, **N/A** dizesi Kullanıcı Arabirimi'nde görüntülenir.

 Her çözümün kendi yapılandırmaları vardır ve bunlardan yalnızca biri aynı anda etkin olabilir. Çözüm yapılandırması, her projeden birden fazla yapılandırma kümesidir. "En fazla" şartı, bir projeyi çözüm yapılandırmasından dışlama seçeneğinden kaynaklanmaktadır. Kullanıcılar kendi özel çözüm yapılandırmalarını oluşturabilir.

 Aşağıdaki tablo, bir proje için tipik yapılandırmalar kurulum gösterir. Satırlar yapılandırma adları ve platform adları içeren sütunlarla etiketlenir.

|Yapılandırma adı|Platform: Win32|Platform: Win64|
|------------------------|----------------------|----------------------|
|*Hata ayıklama*|\<Hata Ayıklama Win32 ayarları>|\<Hata Win64 ayarları>|
|*Yayınla*|\<Win32 ayarlarını> yayınlayın|\<Win64 ayarlarını> yayınlayın|
|*MyConfig*|Yok|\<MyConfig Win64 ayarları>|

> [!NOTE]
> Hedeflediğiniz proje Win32'yi desteklemediği sürece Win32 platformlarını hariç tutan bir *MyConfig* çözüm yapılandırması oluşturamazsınız.

 Bir çözüm için etkin yapılandırmayı değiştirmek, bu çözümde oluşturulmuş, çalıştırılan, debugged veya dağıtılan proje yapılandırmaları kümesini seçer. Örneğin, etkin çözüm yapılandırmasını *Release'den* *Hata Ayıklama'ya*değiştirirseniz, bu çözümdeki tüm projeler, çözümün hata ayıklama yapılandırmasında belirtilen projelerin yapılandırmasıyla otomatik olarak oluşturulur. Kullanıcı ortamın Configuration Manager'ında el ile değişiklik yapmadıysanız, projelerin yapılandırmaları *hata ayıklama* olarak da adlandırılır.

 Her proje için depolanan çözüm yapılandırma özellikleri, proje adını, proje yapılandırma adını, yapının veya dağıtılmayacağını belirtmek için bayraklar ve platform adını içerir. Daha fazla bilgi için [Çözüm yapılandırması'na](../../extensibility/internals/solution-configuration.md)bakın.

 Kullanıcı, hiyerarşideki çözümü (Çözüm Gezgini) seçerek ve özellik sayfalarını açarak çözüm yapılandırma parametrelerini görüntüleyebilir ve ayarlayabilir. Benzer şekilde, Solution Explorer'da bir proje seçerek ve bu projenin özellik sayfalarını açarak proje yapılandırma parametrelerini görüntüleyebilir ve ayarlayabilirsiniz.

 Kullanıcı ayrıca sürüm yapılandırma ayarlarını ve gerekirse hata ayıklama yapılandırma ayarları ile geri kalan tüm sürümü kullanarak bir proje oluşturabilirsiniz. Daha fazla bilgi [için, oluşturmak için Proje yapılandırması'na](../../extensibility/internals/project-configuration-for-building.md)bakın.

 Aşağıdaki diyagram, çözüm ve proje yapılandırmalarını destekleyen arabirimlerin nasıl uygulandığını gösterir:

 ![Yapılandırma arabirimleri grafik](../../extensibility/internals/media/vsconfiginterfaces.gif "vsConfigInterfaces") Yapılandırma arabirimleri

 Önceki diyagramla ilgili birkaç not:

- `IDispatch`yapılandırma nesnesinde isteğe bağlı olarak işaretlenir. Özellikle, gözatma nesnesi üzerinde yapılandırma arabirimleri olması isteğe bağlıdır.

- `IVsDebuggableProjectCfg`yapılandırma nesnesinde isteğe bağlı olarak işaretlenir, ancak hata ayıklama desteği için gereklidir.

- `IVsProjectCfg2`yapılandırma nesnesinde isteğe bağlı olarak işaretlenir, ancak çıktı gruplandırma desteği için gereklidir.

- Config Sağlayıcı nesnesi isteğe bağlı bir nesne olarak işaretlenir, ancak seçenek nerede uygulanacağıdır. Nesneyi proje nesnesi üzerinde veya ayrı bir nesne üzerinde uygulayabilirsiniz.

- `IVsCfgProvider2`platform desteği ve yapılandırma düzenlemesi için gereklidir. `IVsCfgProvider`bu işlevi uygulamazsanız yeterlidir.

- Diyagramda ayrı nesneler olarak gösterilen bu nesnelerden bazıları, belirli tasarım gereksinimlerinize göre pratik olan aynı sınıfa birleştirilebilir. Ancak bu bölümün diğer bölümlerinde, bu nesnelerle ilişkili nesneler ve arabirimler diyagramda sunulan senaryoya göre ele alınacaktır.

- Bazı nesneler ayrı olarak uygulanır. Örneğin, proje ve çözüm oluşturma ayrı iş parçacıkları üzerinde oluşur ve yapı yı yönetmek için nesne yapı yapılandırmasını açıklayan nesneden ayrı yaşıyor.

  Önceki diyagramdaki yapılandırma nesne arabirimleri ve yapılandırma sağlayıcısı nesne arabirimleri hakkında daha fazla bilgi için [Project yapılandırma nesnesi konusuna](../../extensibility/internals/project-configuration-object.md)bakın. Buna ek olarak, [yapı için Proje yapılandırması](../../extensibility/internals/project-configuration-for-building.md) Yapılandırma oluşturucusu ve yapı bağımlılık nesnesi arabirimleri hakkında daha fazla bilgi sağlar ve [dağıtımı yönetmek için Project yapılandırması](../../extensibility/internals/project-configuration-for-managing-deployment.md) yapılandırma dağıtıcı ve dağıtım bağımlılık nesnelerine eklenen arabirimleri daha da açıklar. Son olarak, [çıktı için Project yapılandırması](../../extensibility/internals/project-configuration-for-output.md) çıktı grubu ve çıktı nesnesi arabirimlerini ve yapılandırmaya bağlı özellikleri görüntülemek ve ayarlamak için özellik sayfalarının kullanımını açıklar.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>
- [Bina için proje yapılandırması](../../extensibility/internals/project-configuration-for-building.md)
- [Çözüm yapılandırması](../../extensibility/internals/solution-configuration.md)
