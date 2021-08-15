---
title: Türleri görsel tasarımcılara sunma | Microsoft Docs
description: özel araçlardır dahil olmak üzere sınıf ve tür tanımlarını kullanıma sunma hakkında bilgi edinin. bu sayede, Visual Studio görsel tasarımcılar tarafından kullanılabilir hale getirebilir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- types [Visual Studio SDK], exposing to visual designers
- designers [Visual Studio SDK], exposing types
- custom tools, exposing types to visual designers
ms.assetid: a7a32ad4-3a0a-4eb8-a6ac-491c42885639
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 0e3df8f3bba405c6757260c8991a4a07ca2f1059ea2d0c2a7ae297550b065b19
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121448097"
---
# <a name="expose-types-to-visual-designers"></a>Türleri görsel tasarımcılara sunun
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] görsel bir tasarımcıyı göstermek için tasarım zamanında sınıf ve tür tanımlarına erişimi olmalıdır. Sınıflar, geçerli projenin tüm bağımlılık kümesini (başvurular artı bunların bağımlılıkları) içeren önceden tanımlanmış bir derleme kümesinden yüklenir. Görsel tasarımcılarının özel araçlar tarafından oluşturulan dosyalarda tanımlanan sınıflara ve türlere erişmesi de gerekebilir.

 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]Ve [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] Proje sistemleri, geçici taşınabilir yürütülebilir dosyalar (geçici pes) aracılığıyla oluşturulan sınıflara ve türlere erişim desteği sağlar. Özel bir araç tarafından oluşturulan herhangi bir dosya, türlerin bu derlemelerden yüklenebilmesi ve tasarımcılara sunulanabilmesi için geçici bir derlemeye derlenebilir. Her bir özel aracın çıkışı ayrı bir geçici PE 'de derlenir ve bu geçici derlemenin başarısı veya başarısızlığı, yalnızca oluşturulan dosyanın derlenebilir olup olmamasına bağlıdır. Bir proje bir bütün olarak derlenmese de, tek tek geçici PEs, tasarımcılar tarafından kullanılabilir olmaya devam edebilir.

 Proje sistemi, özel bir aracın çıkış dosyasında yapılan değişiklikleri izlemek için tam destek sağlar, bu değişiklikler özel aracı çalıştırmanın sonucudur. Özel araç her çalıştırıldığında, yeni bir geçici PE oluşturulur ve uygun bildirimler tasarımcılara gönderilir.

> [!NOTE]
> Geçici program yürütülebilir oluşturma dosyası arka planda yapıldığından, derleme başarısız olursa kullanıcıya herhangi bir hata bildirilmemiştir.

 Geçici PE desteğinden faydalanan özel araçlar aşağıdaki kurallara uymalıdır:

- **GeneratesDesignTimeSource** , kayıt defterinde 1 olarak ayarlanmalıdır.

     Bu ayar olmadan hiçbir program yürütülebilir dosya derlemesi gerçekleşmez.

- Oluşturulan kod, genel proje ayarıyla aynı dilde olmalıdır.

     Geçici PE, özel araç tarafından istenen uzantı olarak rapor edilir ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> Bu durum kayıt defterinde **GeneratesDesignTimeSource** 'in 1 olarak ayarlanması şartıyla derlenir. Uzantının *. vb*, *. cs* veya *. jsl*; olması gerekmez. herhangi bir uzantı olabilir.

- Özel araç tarafından oluşturulan kod geçerli olmalıdır ve yalnızca, yürütme tamamlandığında projede bulunan başvuruların kümesi kullanılarak derlenmelidir <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> .

     Geçici bir PE derlendiğinde, derleyiciye sunulan tek kaynak dosya özel araç çıktıdır. Bu nedenle, geçici bir PE kullanan özel bir araç, projedeki diğer dosyalardan bağımsız olarak derlenebilecek çıkış dosyaları üretmelidir.

## <a name="see-also"></a>Ayrıca bkz.
- [BuildManager nesnesine giriş](/previous-versions/8f9kffa8(v=vs.140))
- [Tek dosya oluşturucularını uygulama](../../extensibility/internals/implementing-single-file-generators.md)
- [Tek dosya oluşturucularını Kaydet](../../extensibility/internals/registering-single-file-generators.md)