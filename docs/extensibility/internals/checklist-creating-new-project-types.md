---
title: 'Denetim Listesi: Yeni Proje Türleri Oluşturma | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating new types
- project types, checklist for creating
ms.assetid: 29eb9c3b-1933-4741-aa85-65a33f0825ba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5963083239571af43012e1a79576ee80846d80bd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709746"
---
# <a name="checklist-create-new-project-types"></a>Denetim Listesi: Yeni proje türleri oluşturma
Yeni bir proje türü oluşturmak için birkaç görevi tamamlamanız gerekir. Aşağıdaki denetim listesi bu görevler için bir kılavuz sağlar:

1. Yeni proje türünüz için işlevselliği tasarla. Daha fazla bilgi için [Proje türü tasarım kararlarına](../../extensibility/internals/project-type-design-decisions.md)bakın.

2. Kod ve diğer proje öğeleri için hangi düzenleyicilerin kullanıldığını belirleyin. Çekirdek veya standart düzenleyicileri kullanabilir veya projeye özel düzenleyiciler oluşturabilir ve kullanabilirsiniz. Daha fazla bilgi için bkz: [Özel düzenleyiciler ve tasarımcılar oluştur](../../extensibility/creating-custom-editors-and-designers.md) ve nasıl [açılır: Projeye özel düzenleyicileri açın.](../../extensibility/how-to-open-project-specific-editors.md)

3. Proje öğelerinizin **Sınıf Görünümü'nde** ve Nesne **Tarayıcısında**sahip olacağı katılım düzeyini belirleyin. Daha fazla bilgi için destek [simgesi tarama araçlarına](../../extensibility/internals/supporting-symbol-browsing-tools.md)bakın.

4. Projeniz ve proje öğeleriniz için daha önce yapmış olduğunuz tasarım kararlarına dayalı yeni sınıflar türetin.

5. Aşağıdaki proje türü bileşenleri için kodu yazın:

    - Proje fabrikası, yeni projeler oluşturma ve mevcut projeleri açma yönetmek. Daha fazla bilgi için [bkz.](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)

    - Proje hiyerarşisi ve komut işleme. Daha fazla bilgi için, [bir proje türü (C++) uygulamak için HierUtil7 proje sınıflarını kullanın](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346), proje [modelinin öğeleri,](../../extensibility/internals/elements-of-a-project-model.md) [Proje modeli temel bileşenleri](../../extensibility/internals/project-model-core-components.md)ve [MenuCommands vs OleMenuCommands](/visualstudio/extensibility/menucommands-vs-olemenucommands?view=vs-2015)bakın.

    - Projenizi **Yeni Proje** iletişim kutusuna eklemek de dahil olmak üzere proje öğeleri yönetimi. Daha fazla bilgi için bkz. [Proje ve proje öğesi şablonları ekle](../../extensibility/internals/adding-project-and-project-item-templates.md) ve proje ve madde [şablonlarını kaydedin.](../../extensibility/internals/registering-project-and-item-templates.md)

    - Proje durumunun ve tek tek öğelerin kalıcılığı. Daha fazla bilgi için [açık ve proje öğelerini kaydet'e](../../extensibility/internals/opening-and-saving-project-items.md)bakın. Çözüm bilgilerinin kalıcılığı için [Çözümler](../../extensibility/internals/solutions-overview.md)bölümüne bakın.

    - Özellikler penceresinde görüntülenecek yapılandırmadan bağımsız özellikler. Daha fazla bilgi için [bkz.](../../extensibility/internals/extending-properties.md)

    - Yapılandırmaya bağımlı özellikleri göstermek için özellik sayfalarında uygulanan yapılandırma özelliklerini yansıtın. Daha fazla bilgi için [bkz.](../../extensibility/internals/managing-configuration-options.md)

    - Dağıtım için çıktıları sayısallaştırıyor. Daha fazla bilgi [için çıktı için Proje yapılandırması'na](../../extensibility/internals/project-configuration-for-output.md)bakın.

    - Proje başlangıç hizmetleri. Daha fazla bilgi için [bkz.](../../extensibility/internals/elements-of-a-project-model.md) [Project model core components](../../extensibility/internals/project-model-core-components.md)

    - Otomasyon için kullanılabilir `IDispatch`nesneler veya türetilen sınıflar.

    - XML komut tablosu (*.vsct*) dosyaları. Daha fazla bilgi için [Visual Studio komut tablosu (.vsct) dosyalarına](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)bakın.

6. Test edin, hata ayıklatın ve proje türünü başlatın.

7. Projenizi **Başvuru Ekle** iletişim kutusunun **Proje** sekmesinde `VARIANT_TRUE` değerini ayarlayarak görüntüleyin. `VSHPROPID_ShowProjInSolutionPage` Daha fazla bilgi için <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> bölümlerine bakın.

8. VSPackages'ınızı yüklemek için Microsoft Installer (*.msi*) dosyasını oluşturun. Daha fazla bilgi için Windows [Installer ile VSPackages Yükle,](../../extensibility/internals/installing-vspackages-with-windows-installer.md) [Proje türünü kaydedin](../../extensibility/internals/registering-a-project-type.md)ve [VSPackages'e](../../extensibility/internals/vspackages.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio’da Hiyerarşiler](../../extensibility/internals/hierarchies-in-visual-studio.md)
- [Proje türleri ne zaman oluşturulacak?](../../extensibility/internals/when-to-create-project-types.md)
- [Proje türleri oluşturma](../../extensibility/internals/creating-project-types.md)
