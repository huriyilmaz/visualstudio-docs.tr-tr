---
title: Project Yapı Yapılandırma | Microsoft Docs
description: Belirli bir çözüm için çözüm yapılandırmalarının listesinin yeni bir proje türü içinde Çözüm Yapılandırmaları iletişim kutusu tarafından nasıl yönetil olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- projects [Visual Studio SDK], configuration for building
- project configurations, building
ms.assetid: 2c83615d-fa4d-4b9f-b315-7a69b3000da0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 3ef4ab11bd4f5dca68e07a3084371024728336e1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122049772"
---
# <a name="project-configuration-for-building"></a>Derleme için Proje Yapılandırması
Verilen bir çözümün çözüm yapılandırmalarının listesi, Çözüm Yapılandırmaları iletişim kutusu tarafından yönetilir.

 Bir kullanıcı, her biri kendi benzersiz adına sahip ek çözüm yapılandırmaları oluşturabilir. Kullanıcı yeni bir çözüm yapılandırması oluşturduğunda, IDE varsayılan olarak projelerde karşılık gelen yapılandırma adını veya karşılık gelen bir ad yoksa Hata Ayıkla'ya karşılık gelen adı kullanır. Kullanıcı, gerekirse belirli gereksinimleri karşılamak için seçimi değiştirebilir. Bu davranışın tek istisnası, projenin yeni çözüm yapılandırmasının adıyla eşleşen bir yapılandırmayı desteklemesidir. Örneğin, bir çözümün Project1 ve Project2 içerdiğini varsayalım. Project1'de Hata Ayıklama, Perakende ve MyConfig1 proje yapılandırmaları vardır. Project2'de Hata Ayıklama, Perakende ve MyConfig2 proje yapılandırmaları vardır.

 Kullanıcı MyConfig2 adlı yeni bir çözüm yapılandırması oluşturursa, Project1 hata ayıklama yapılandırmasını varsayılan olarak çözüm yapılandırmasına bağlar. Project2 ayrıca MyConfig2 yapılandırmasını varsayılan olarak çözüm yapılandırmasına bağlar.

> [!NOTE]
> Bağlama büyük/büyük/büyük harfe duyarlı değildir.

 Kullanıcı yapılandırma açılan listesinde **Birden** Çok Seçim öğesini seçerken, ortam kullanılabilir yapılandırmaların listesini sağlayan bir iletişim kutusu görüntüler.

 ![Birden Çok Yapılandırma](../../extensibility/internals/media/vsmultiplecfgs.gif "vsMultipleCfgs") Birden çok yapılandırma

 Bu iletişim kutusunda kullanıcı bir veya birden çok yapılandırmayı belirleyebilir. Seçildikten sonra, özellik sayfaları iletişim kutusunda görüntülenen özellik değerleri, seçilen yapılandırmalar için değerlerin kesişimlerini gösterir.

 Çözümler [ve projeler](../../extensibility/internals/solution-configuration.md) için yapılandırmaları ekleme ve yeniden markalama hakkında bilgi için bkz. Çözüm Yapılandırması.

 Project ve derleme sırası çözüm yapılandırmasına bağımsızdır. Başka bir ifadeyle çözümde yer alan tüm projeler için yalnızca bir bağımlılık ağacı kurarak bu bağımlılık ağacını kuracağız. Çözüme veya projeye sağ tıklar  ve Project Bağımlılıklar  veya Project Derleme Sırası seçeneğinin Project **iletişim kutusu** açılır. Bu menü, Project **de** açılabilir.

 ![Project Bağımlılıklar](../../extensibility/internals/media/vsprojdependencies.gif "vsProjDependencies") Project bağımlılıkları

 Project bağımlılıkları projelerin derleme sırası belirler. Bir çözüm içindeki projelerin derleme sırası tam olarak görüntülemek için iletişim kutusundaki Derleme Sırası sekmesini kullanın ve derleme siparişini değiştirmek için Bağımlılıklar sekmesini kullanın.

> [!NOTE]
> Listede onay kutularının seçili olduğu ancak soluk görünen projeler, veya arabirimleri tarafından belirtilen açık bağımlılıklar nedeniyle ortam tarafından eklenmiştir <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> ve değiştirilemez. Örneğin, bir projeden başka bir projeye proje başvurusu eklemek, otomatik olarak yalnızca başvuru silinerek [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] kaldırılabilir bir derleme bağımlılığı ekler. Onay kutuları temiz ve soluk görünen projeler seçilebilmelidir çünkü bunu yapmak bir bağımlılık döngüsü (örneğin, Project1 Project2'ye bağımlı olur ve Project2, Project1'e bağımlı olur) ve bu da derlemeyi duraklar.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] derleme işlemleri, tek bir Derleme komutuyla çağrılan tipik derleme ve bağlantı işlemlerini içerir. Diğer iki derleme işlemi de destek olabilir: önceki derlemeden tüm çıkış öğelerini silmek için temiz bir işlem ve yapılandırmadaki bir çıktı öğesinin değiştirilebilir olup olmadığını belirlemek için güncel bir denetim.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> nesneleri, derleme işlemlerini <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> yönetmek için karşılık gelen bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A> ('den döndürülür) döndürülür. Bir derleme işlemi meydana geldiği sırada durumunu rapor etmek için yapılandırmalar, ortam tarafından uygulanan bir arabirime ve derleme durumu olaylarıyla ilgilenen diğer <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildStatusCallback> nesnelere çağrılar oluşturur.

 Yapılandırma ayarları, bir kez yapılandırmasını yapılandırarak hata ayıklayıcı denetimi altında çalıştırılap çalıştırılamaylarını belirlemek için kullanılabilir. Yapılandırmalar hata <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> ayıklamayı desteklemek için uygulanır.

 Proje bağımlılıklarını uygulamaya başladıktan sonra, bağımlılıkları otomasyon modeli aracılığıyla program aracılığıyla işabilirsiniz. Otomasyon <xref:EnvDTE.SolutionBuild.BuildDependencies%2A> modelinde çağrısında bulundurun. Çözüm derleme yöneticisi yapılandırmalarının ve özelliklerinin doğrudan işlemesine olanak sağlayan kullanılabilir VSIP API düzeyinde arabirim yoktur.

 Ayrıca, proje bağımlılıkları penceresinde bir kılavuz sabilirsiniz. Daha fazla bilgi için bkz. [Özellikler Display Grid](../../extensibility/internals/properties-display-grid.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılandırma Seçeneklerini Yönetme](../../extensibility/internals/managing-configuration-options.md)
- [Dağıtımı Yönetmek için Proje Yapılandırması](../../extensibility/internals/project-configuration-for-managing-deployment.md)
- [Çıkış için Proje Yapılandırması](../../extensibility/internals/project-configuration-for-output.md)
