---
title: Görsel Tasarımcılara Türleri Teşhir Etme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- types [Visual Studio SDK], exposing to visual designers
- designers [Visual Studio SDK], exposing types
- custom tools, exposing types to visual designers
ms.assetid: a7a32ad4-3a0a-4eb8-a6ac-491c42885639
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9067f88b4bf1334e23a548bc6a2cbeb3eac6ad33
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708433"
---
# <a name="expose-types-to-visual-designers"></a>Türleri görsel tasarımcılara gösterin
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]görsel bir tasarımcıyı görüntülemek için tasarım zamanında sınıf ve tür tanımlarına erişebilmeli. Sınıflar, geçerli projenin tam bağımlılık kümesini (başvurular ve bunların bağımlılıklarını) içeren önceden tanımlanmış bir derleme kümesinden yüklenir. Ayrıca, görsel tasarımcıların özel araçlar tarafından oluşturulan dosyalarda tanımlanan sınıflara ve türlere erişmeleri de gerekebilir.

 Ve [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] proje sistemleri, geçici taşınabilir yürütülebilir dosyalar (geçici P'ler) aracılığıyla oluşturulan sınıflara ve türlere erişmek için destek sağlar. Özel bir araç tarafından oluşturulan herhangi bir dosya, bu derlemelerden türlerin yüklenebileceği ve tasarımcılara açıklanabilmesi için geçici bir derlemede derlenebilir. Her özel aracın çıktısı ayrı bir geçici PE olarak derlenir ve bu geçici derlemenin başarısı veya başarısızlığı yalnızca oluşturulan dosyanın derlenip derlenemeyeceğine bağlıdır. Bir proje bir bütün olarak inşa olmayabilir, her ne kadar bireysel geçici PEs hala tasarımcılar için kullanılabilir olabilir.

 Proje sistemi, bu değişikliklerin özel aracı çalıştırmanın sonucu olması koşuluyla, özel bir aracın çıktı dosyasındaki değişiklikleri izlemek için tam destek sağlar. Özel araç her çalıştırılsa, yeni bir geçici PE oluşturulur ve tasarımcılara uygun bildirimler gönderilir.

> [!NOTE]
> Geçici program yürütülebilir oluşturma dosyası arka planda gerçekleştiğinden, derleme başarısız olursa kullanıcıya hata bildirilir.

 Geçici PE desteğinden yararlanan özel araçlar aşağıdaki kurallara uymalıdır:

- **OluştururDesignTimeSource** kayıt defterinde 1 olarak ayarlanmalıdır.

     Bu ayar olmadan hiçbir program yürütülebilir dosya derlemesi gerçekleşmez.

- Oluşturulan kod, genel proje ayarı ile aynı dilde olmalıdır.

     Geçici PE, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> **GeneratesDesignTimeSource'un** kayıt defterinde 1 olarak ayarlanması koşuluyla, istenen uzantı olarak özel araç raporlarıne bakılmaksızın derlenir. Uzantısı *.vb*, *.cs*veya *.jsl*olması gerekmez; herhangi bir uzantısı olabilir.

- Özel araç tarafından oluşturulan kod geçerli olmalıdır ve yürütmeyi bitirdiği sırada <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> projede bulunan başvuru kümesini kullanarak kendi başına derlemesi gerekir.

     Geçici bir PE derlendiğinde, derleyiciye sağlanan tek kaynak dosya özel araç çıkışıdır. Bu nedenle, geçici bir PE kullanan özel bir araç, projedeki diğer dosyalardan bağımsız olarak derlenebilen çıktı dosyaları oluşturması gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [BuildManager nesnesine giriş](https://msdn.microsoft.com/library/50080ec2-c1c9-412c-98ef-18d7f895e7fa)
- [Tek dosyalı jeneratörleri uygulama](../../extensibility/internals/implementing-single-file-generators.md)
- [Tek dosyalı jeneratörleri kaydetme](../../extensibility/internals/registering-single-file-generators.md)
