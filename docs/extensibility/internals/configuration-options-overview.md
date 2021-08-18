---
title: Yapılandırma seçeneklerine genel bakış | Microsoft Docs
description: Visual Studio içindeki proje yapılandırmalarına yönelik seçenekler hakkında bilgi edinin. Yapılandırma, adlandırılmış özellikler ve dosya konumları kümesiyle tanımlanan bir yapı türüdür.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations
- configuration options, about configuration options
ms.assetid: f4ad4dd3-b39e-42df-ad89-d403cdf24a2b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 0bde8342961136cddf5a89bb5799abacef462e5a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122028975"
---
# <a name="configuration-options-overview"></a>Yapılandırma seçeneklerine genel bakış
İçindeki projeler [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , derlenen, hata ayıklaması yapılan, çalıştırılan ve/veya dağıtılan birden fazla yapılandırmayı destekleyebilir. Yapılandırma, genellikle derleyici anahtarları ve dosya konumları gibi adlandırılmış özellikler kümesiyle tanımlanan bir yapı türüdür. Varsayılan olarak, yeni çözümler iki yapılandırma, *hata ayıklama* ve *yayın* içerir. Bu yapılandırma, varsayılan ayarları kullanılarak uygulanabilir veya özel çözümünüzü ve/veya proje gereksinimlerinizi karşılayacak şekilde değiştirilebilir. bazı paketler iki şekilde oluşturulabilir: ActiveX düzenleyicisi olarak veya yerinde bileşen olarak. Ancak projelerin birden çok yapılandırmayı desteklemesi gerekmez. Yalnızca bir yapılandırma varsa, bu yapılandırma tüm çözüm yapılandırmalarına eşlenir.

 Yapılandırmalar genellikle iki bölümden oluşur: yapılandırma adı (örneğin, *hata ayıklama* veya *Sürüm*) ve platform ayarları. Yapılandırmanın platform adı, API kümesi veya işletim sistemi platformu gibi yapılandırmanın hedeflediği ortamı tanımlar. Kullanıcıları [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bir platform oluşturamaz; bir proje VSPackage izin verdiği seçimlerde seçim yapmanız gerekir. Bir Kullanıcı VSPackage yüklediğinde, paketin geliştirilmesi sırasında oluşturulan dağıtım platformu, paket Oluşturucu tarafından ayarlanan ölçütlere göre istenen platform adlarını de açabilir. Kullanıcı daha sonra özellik sayfaları örnekleniken VSPackage aracılığıyla kullanılabilir hale getirilen platformlar listesinden seçim yapabilir.

 Tüm projeler platformların kavramını desteklemediğinden, platform adları isteğe bağlıdır. Bir yapılandırma bir platform adı olmadığında, Kullanıcı arabiriminde **N/a** dizesi görüntülenir.

 Her çözümün kendi yapılandırma kümesi vardır, tek seferde yalnızca biri etkin olabilir. Çözüm yapılandırması, her projeden birden fazla yapılandırma değildir. "Şundan fazla bilgi yok" seçeneği, bir projeyi çözüm yapılandırmasından hariç tutma seçeneği nedeniyle yapılır. Kullanıcılar kendi özel çözüm yapılandırmalarının oluşturulmasını sağlayabilir.

 Aşağıdaki tabloda bir proje için tipik yapılandırma ayarları gösterilmektedir. Satırlar yapılandırma adlarıyla ve platform adları olan sütunlarla etiketlenir.

|Yapılandırma adı|Platform: Win32|Platform: Win64|
|------------------------|----------------------|----------------------|
|*Hata Ayıklama*|\<Debug Win32 settings>|\<Debug Win64 settings>|
|*Sürüm*|\<Release Win32 settings>|\<Release Win64 settings>|
|*MyConfig*|Yok|\<MyConfig Win64 settings>|

> [!NOTE]
> Hedeflenmediğiniz proje Win32 'yi desteklemiyorsa Win32 platformunu dışlayan bir *MyConfig* çözüm yapılandırması oluşturamazsınız.

 Bir çözüm için etkin yapılandırmanın değiştirilmesi, bu çözümde oluşturulan, çalıştırılan, hata ayıklanan veya dağıtılan proje yapılandırmaları kümesini seçer. Örneğin, etkin çözüm yapılandırmasını *yayından* *hata ayıklama* olarak değiştirirseniz, bu Çözümdeki tüm projeler, çözümün hata ayıklama yapılandırmasında belirtilen proje yapılandırmasıyla otomatik olarak oluşturulur. Kullanıcının, ortamın Configuration Manager el ile değişiklikler yapmadığı müddetçe, proje yapılandırmalarına da *hata ayıklama* adı verilir.

 Her proje için depolanan çözüm yapılandırma özellikleri proje adı, proje yapılandırma adı, bayrak oluşturulup oluşturulmayacağını veya dağıtılacağını ve platform adının ne olduğunu belirten bayrakları içerir. Daha fazla bilgi için bkz. [çözüm yapılandırması](../../extensibility/internals/solution-configuration.md).

 Kullanıcı, hiyerarşide çözümü seçerek (Çözüm Gezgini) ve özellik sayfalarını açarak çözüm yapılandırma parametrelerini görüntüleyebilir ve ayarlayabilir. Benzer şekilde, proje yapılandırma parametrelerini, Çözüm Gezgini bir proje seçerek ve bu projenin özellik sayfalarını açarak görüntüleyebilir ve ayarlayabilirsiniz.

 Kullanıcı aynı zamanda yayın yapılandırma ayarlarını ve gerekirse hata ayıklama yapılandırma ayarlarıyla tüm rest 'yi kullanarak bir proje oluşturabilir. daha fazla bilgi için bkz. [derleme için Project yapılandırma](../../extensibility/internals/project-configuration-for-building.md).

 Aşağıdaki diyagramda çözümü ve proje yapılandırmasını destekleyen arabirimlerin nasıl uygulandığı gösterilmektedir:

 ![Yapılandırma arabirimleri grafiği](../../extensibility/internals/media/vsconfiginterfaces.gif "Vsconfigınterfaces") Yapılandırma arabirimleri

 Önceki diyagramla ilgili birkaç Not:

- `IDispatch` yapılandırma nesnesinde isteğe bağlı olarak işaretlenir. Özellikle, tarama nesnesi üzerinde yapılandırma arabirimlerini sağlamak isteğe bağlıdır.

- `IVsDebuggableProjectCfg` yapılandırma nesnesinde isteğe bağlı olarak işaretlenir, ancak hata ayıklama desteği için gereklidir.

- `IVsProjectCfg2` yapılandırma nesnesinde isteğe bağlı olarak işaretlenir, ancak çıkış gruplama desteği için gereklidir.

- Yapılandırma sağlayıcısı nesnesi, isteğe bağlı bir nesne olarak işaretlenir, ancak bunu uygulamak için bir seçenek vardır. Nesneyi proje nesnesi üzerinde veya ayrı bir nesne üzerinde uygulayabilirsiniz.

- `IVsCfgProvider2` Platform desteği ve yapılandırma düzenlemesi için gereklidir. `IVsCfgProvider` Bu işlevi uygulamadıysanız yeterlidir.

- Diyagramda ayrı nesneler olarak gösterilen bu nesnelerden bazıları, özel tasarım gereksinimlerinize göre pratik olarak aynı sınıfta birleştirilebilir. Ancak, bu bölümün diğer konularında, bu nesnelerle ilişkili nesneler ve arabirimler diyagramda sunulan senaryoya göre ele alınacaktır.

- Belirli nesneler ayrı ayrı uygulanır. Örneğin, proje ve çözüm oluşturma ayrı iş parçacıklarında ve derlemeyi yöneten nesne, derleme yapılandırmasını açıklayan nesneden ayrı olarak gerçekleşir.

  önceki diyagramda yapılandırma nesnesi arabirimleri ve yapılandırma sağlayıcısı nesne arabirimleri hakkında daha fazla bilgi için bkz. [Project configuration nesnesi](../../extensibility/internals/project-configuration-object.md). ayrıca, [oluşturma için Project yapılandırma](../../extensibility/internals/project-configuration-for-building.md) , configuration builder ve derleme bağımlılığı nesne arabirimleri hakkında daha fazla bilgi sağlar ve [dağıtımı yönetmeye yönelik Project yapılandırma](../../extensibility/internals/project-configuration-for-managing-deployment.md) , yapılandırma dağıtıcı ve dağıtım bağımlılığı nesnelerine eklenen arabirimleri daha da açıklar. son olarak, [çıkış için Project yapılandırma](../../extensibility/internals/project-configuration-for-output.md) , çıkış grubunu ve çıkış nesnesi arabirimlerini ve yapılandırma bağımlı özellikleri görüntülemek ve ayarlamak için özellik sayfalarının kullanımını açıklar.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>
- [oluşturma için Project yapılandırması](../../extensibility/internals/project-configuration-for-building.md)
- [Çözüm yapılandırması](../../extensibility/internals/solution-configuration.md)
