---
title: Çıktı için Proje Yapılandırması | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, output
ms.assetid: a4517f73-45af-4745-9d7f-9fddf887b636
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 78b95457af4c5d806fdfcc20f49ac4e82df36488
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706665"
---
# <a name="project-configuration-for-output"></a>Çıkış için Proje Yapılandırması
Her yapılandırma, yürütülebilir veya kaynak dosyaları gibi çıktı öğeleri üreten bir yapı işlemleri kümesini destekleyebilir. Bu çıktı öğeleri kullanıcıya özeldir ve yürütülebilir dosyalar (.exe, .dll, .lib) ve kaynak dosyaları (.idl, .h dosyaları) gibi ilgili çıktı türlerini birbirine bağlayan gruplara yerleştirilebilir.

 Çıkış maddeleri <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2> metotlarla kullanılabilir hale getirilebilir <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs> ve metotlarla numaralandırılabilir. Çıktı öğelerini gruplandırmak istediğinizde, projeniz in arabirimi <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> de uygulamalıdır.

 Uygulanarak `IVsOutputGroup` geliştirilen yapı, projelerin çıktıları kullanıma göre gruplandırmasına olanak sağlar. Örneğin, bir DLL program veritabanı (PDB) ile gruplandırılabilir.

> [!NOTE]
> PDB dosyası hata ayıklama bilgilerini içerir ve .dll veya .exe'yi oluştururken 'Hata Ayıklama Bilgisi Oluştur' seçeneği belirtildiğinde oluşturulur. .pdb dosyası genellikle yalnızca Hata Ayıklama proje yapılandırması için oluşturulur.

 Bir grup içinde bulunan çıktı sayısı yapılandırmadan yapılandırmaya değişse de, proje desteklediği her yapılandırma için aynı sayıda grup döndürmelidir. Örneğin, Matt'in DLL projesi Hata Ayıklama yapılandırmasında mattd.dll ve mattd.pdb'yi içerebilir, ancak yalnızca Perakende yapılandırmasında matt.dll'yi içerebilir.

 Gruplar ayrıca, bir proje içinde yapılandırmadan yapılandırmaya kadar kanonik ad, görüntü adı ve grup bilgileri gibi aynı tanımlayıcı bilgilerine de sahiptir. Bu tutarlılık, yapılandırmalar değişse bile dağıtım ve paketlemenin çalışmaya devam etmesini sağlar.

 Gruplar, ambalaj kısayollarının anlamlı bir şeye işaret etmesini sağlayan önemli bir çıktıya da sahip olabilir. Herhangi bir grup belirli bir yapılandırmada boş olabilir, bu nedenle bir grubun boyutu hakkında hiçbir varsayımda bulunulmaması gerekir. Herhangi bir yapılandırmadaki her grubun boyutu (çıktı sayısı) aynı yapılandırmadaki başka bir grubun boyutundan farklı olabilir. Ayrıca, başka bir yapılandırmada aynı grubun boyutundan farklı olabilir.

 ![Çıktı Grupları grafiği](../../extensibility/internals/media/vsoutputgroups.gif "vsOutputGroups") Çıktı grupları

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg> Arabirimin birincil kullanımı, yönetim nesnelerini oluşturmaya, dağıtmaya ve hata ayıklamalarına erişim sağlamak ve projelere çıktıları gruplandırma özgürlüğü sağlamaktır. Bu arabirimin kullanımı hakkında daha fazla bilgi için [Project Configuration Object](../../extensibility/internals/project-configuration-object.md)bölümüne bakın.

 Önceki diyagramda, Grup Yapısı yapılandırmaları arasında önemli bir çıktıya sahiptir (bD.exe veya b.exe) böylece kullanıcı Yerleşik'e bir kısayol oluşturabilir ve kısayol'un dağıtılan yapılandırmadan bağımsız olarak çalışacağını bilebilir. Grup Kaynağı'nın anahtar çıktısı yoktur, bu nedenle kullanıcı bir kısayol oluşturamaz. Yapılan Hata Ayıklama Grubu önemli bir çıktıya sahipse, ancak Yapılamayan Perakende Grubu yoksa, bu yanlış bir uygulama olur. Daha sonra, herhangi bir yapılandırmada çıktı içermeyen bir grup varsa ve sonuç olarak anahtar dosyası yoksa, çıktıları içeren bu grupla diğer yapılandırmaların anahtar dosyaları olamaz. Yükleyici düzenleyiciler, kanonik adlar ve grup adları, artı anahtar bir dosyanın varlığını, yapılandırmaları dayalı değişmez varsayalım.

 Bir projenin paketlemek `IVsOutputGroup` veya dağıtmak istemediği bir proje varsa, bu çıktıyı bir gruba koymamanın yeterli olduğunu unutmayın. Gruplandırmadan bağımsız olarak, yapılandırmanın <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A> tüm çıktılarını döndüren yöntem uygulanarak çıktı yine de normal olarak numaralandırılabilir.

 Daha fazla bilgi için, `IVsOutputGroup` [Projeler için MPF'de](https://github.com/tunnelvisionlabs/MPFProj10)Özel Proje örneğinde uygulanmasına bakın.

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılandırma Seçeneklerini Yönetme](../../extensibility/internals/managing-configuration-options.md)
- [Derleme için Proje Yapılandırması](../../extensibility/internals/project-configuration-for-building.md)
- [Proje Yapılandırması Nesnesi](../../extensibility/internals/project-configuration-object.md)
- [Çözüm Yapılandırması](../../extensibility/internals/solution-configuration.md)
