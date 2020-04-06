---
title: Proje Modelinin Öğeleri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], implementation considerations
- project models
- projects [Visual Studio SDK], elements
ms.assetid: a1dbe0dc-68da-45d7-8704-5b43ff7e4fc4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf847e35878dc84bb32fe81053c01c23e565fc4c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708530"
---
# <a name="elements-of-a-project-model"></a>Proje modelinin öğeleri
Tüm projelerin arabirimleri ve uygulamaları [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] temel bir yapıyı paylaşır: proje türünüz için proje modeli. Geliştirmekte olduğunuz VSPackage olan proje modelinizde, tasarım kararlarınıza uygun nesneler oluşturur ve IDE tarafından sağlanan genel işlevsellikle birlikte çalışırsınız. Proje öğesinin nasıl kalıcı olduğunu denetlemenize rağmen, örneğin, bir dosyanın kalıcı olması gerektiğine dair bildirimi denetlemezsiniz. Bir kullanıcı açık bir proje öğesine odaklandığında ve **File** [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] menü çubuğundaki Dosya menüsünde **Kaydet'i** seçtiğinde, proje türü kodunuz IDE komutunu durdurmalı, dosyayı devam etti ve dosyanın artık değiştirilmeye niçin IDE'ye bildirim göndermesi gerekir.

 VSPackage'ınız, IDE arabirimlerine erişim sağlayan hizmetler aracılığıyla IDE ile etkileşim kurar. Örneğin, belirli hizmetler aracılığıyla komutları izler ve yönlendirir ve projede yapılan seçimler için bağlam bilgileri sağlarsınız. VSPackage'ınız için gereken tüm küresel IDE işlevselliği hizmetler tarafından sağlanır. Hizmetler hakkında daha fazla bilgi için [bkz.](../../extensibility/how-to-get-a-service.md)

 Diğer uygulama konuları:

- Tek bir proje modeli birden fazla proje türü içerebilir.

- Proje türleri ve katılımcı proje fabrikaları GUID'lere bağımsız olarak kaydedilir.

- Kullanıcı [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Kullanıcı Arabirimi aracılığıyla yeni bir proje oluşturduğunda, her projenin yeni proje dosyasını başlatacak bir şablon dosyası veya sihirbazı olmalıdır. Örneğin, [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] şablonlar sonunda .vcproj dosyaları haline ne başlatılması.

  Aşağıdaki resimde, tipik bir proje uygulaması oluşturan birincil arabirimleri, hizmetleri ve nesneleri gösterilmektedir. Temel nesneleri ve diğer `HierUtil7`programlama kazan plakasını oluşturmak için uygulama yardımcısını kullanabilirsiniz. Uygulama yardımcısı hakkında daha fazla bilgi için, [proje türünü (C++) uygulamak için HierUtil7 proje sınıflarını kullan'a](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)bakın. `HierUtil7`

  ![Visual Studio proje modeli grafiği](../../extensibility/internals/media/vsprojectmodel.gif "vsProjectModel") Proje modeli

  Önceki diyagramda listelenen arabirimler ve hizmetler ve diyagramda yer almayan diğer isteğe bağlı arabirimler hakkında daha fazla bilgi için [Project modeli temel bileşenlerine](../../extensibility/internals/project-model-core-components.md)bakın.

  Projeler komutları destekleyebilir ve <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> bu nedenle komut bağlamı GUIDs üzerinden komut yönlendirme katılmak için arabirimi uygulamak gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Denetim Listesi: Yeni proje türleri oluşturma](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Proje türünü (C++) uygulamak için HierUtil7 proje sınıflarını kullanma](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)
- [Proje modeli çekirdek bileşenleri](../../extensibility/internals/project-model-core-components.md)
- [Proje fabrikalarını kullanarak proje örnekleri oluşturma](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
- [Nasıl yapilir: Hizmet alın](../../extensibility/how-to-get-a-service.md)
- [Proje türleri oluşturma](../../extensibility/internals/creating-project-types.md)
