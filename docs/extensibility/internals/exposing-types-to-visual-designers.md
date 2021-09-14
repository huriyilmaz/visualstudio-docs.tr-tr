---
title: Türleri Görsel Tasarımcılara | Microsoft Docs
description: Özel araçlarda bulunanlar da dahil olmak üzere sınıf ve tür tanımlarını nasıl Visual Studio görsel tasarımcıların kullanmalarına yardımcı olabilir.
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
ms.openlocfilehash: ffee5f17192cc14346f9da52ce32551dea6daded
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725071"
---
# <a name="expose-types-to-visual-designers"></a>Türleri görsel tasarımcıların ortaya çıkarma
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bir görsel tasarımcıyı görüntülemek için tasarım zamanında sınıf ve tür tanımlarına erişimi olması gerekir. Sınıflar, geçerli projenin tam bağımlılık kümesi (başvurular ve bağımlılıkları) içeren önceden tanımlanmış bir derleme kümesinden yüklenir. Görsel tasarımcıların özel araçlar tarafından oluşturulan dosyalarda tanımlanan sınıflara ve türlere erişmesi de gerekebilir.

 ve [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] proje [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] sistemleri, geçici taşınabilir yürütülebilir dosyalar (geçici PE'ler) aracılığıyla oluşturulan sınıflara ve türlere erişim için destek sağlar. Özel bir araç tarafından oluşturulan herhangi bir dosya geçici bir derleme içinde derlenmiş olabilir, böylece türler bu derlemelerden yüklenebilir ve tasarımcılara açık olabilir. Her özel aracın çıkışı ayrı bir geçici PE'de derlenmiş ve bu geçici derlemenin başarılı veya başarısız olması yalnızca oluşturulan dosyanın derlenmesine bağlıdır. Bir proje bütün olarak yapılamasa da, tek tek geçici PE'ler tasarımcılar tarafından kullanılabilir olabilir.

 Proje sistemi, bu değişikliklerin özel aracı çalıştırmanın sonucu olduğu şartıyla, özel bir aracın çıkış dosyasında yapılan değişiklikleri izlemek için tam destek sağlar. Özel araç her çalıştırıldında yeni bir geçici PE oluşturulur ve tasarımcılara uygun bildirimler gönderilir.

> [!NOTE]
> Geçici program yürütülebilir oluşturma dosyası arka planda olduğundan, derleme başarısız olursa kullanıcıya hata bildirmaz.

 Geçici PE desteğinin avantajına sahip özel araçların aşağıdaki kurallara uyması gerekir:

- **GeneratesDesignTimeSource,** kayıt defterinde 1 olarak ayar olmalıdır.

     Bu ayar olmadan program yürütülebilir dosya derlemesi olmaz.

- Oluşturulan kodun genel proje ayarıyla aynı dilde olması gerekir.

     GeneratesDesignTimeSource'ın kayıt defterinde 1 olarak ayarlanmış olduğu sürece, içinde istenen uzantı olarak özel aracın ne raporlediğine bakılmaksızın geçici PE <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> derlenmiş olur.  Uzantının *.vb*, *.cs* veya *.jsl olması gerekir;* herhangi bir uzantı olabilir.

- Özel araç tarafından oluşturulan kodun geçerli olması ve yalnızca projedeki başvuru kümesi yürütücü tamamlansa bile kendi başına <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> derlenmiş olması gerekir.

     Geçici bir PE derlenmiş olduğunda, derleyiciye sağlanan tek kaynak dosya özel araç çıkışıdır. Bu nedenle, geçici PE kullanan özel bir araç, proje içinde diğer dosyalardan bağımsız olarak derlenmiş çıkış dosyaları oluşturması gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [BuildManager nesnesine giriş](/previous-versions/8f9kffa8(v=vs.140))
- [Tek dosya oluşturucuları uygulama](../../extensibility/internals/implementing-single-file-generators.md)
- [Tek dosya oluşturucuları kaydetme](../../extensibility/internals/registering-single-file-generators.md)