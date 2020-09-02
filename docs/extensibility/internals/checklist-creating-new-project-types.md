---
title: 'Denetim listesi: yeni proje türleri oluşturma | Microsoft Docs'
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
ms.openlocfilehash: 9372762f713b6a5ec78a92eeb96e8a616101b5bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "84183398"
---
# <a name="checklist-create-new-project-types"></a>Denetim listesi: yeni proje türleri oluşturma
Yeni bir proje türü oluşturmak için birkaç görevi gerçekleştirmeniz gerekir. Aşağıdaki denetim listesi, bu görevlere rehberlik sağlar:

1. Yeni proje türü için işlevselliği tasarlayın. Daha fazla bilgi için bkz. [Proje türü tasarım kararları](../../extensibility/internals/project-type-design-decisions.md).

2. Hangi düzenleyicilerin kod ve diğer proje öğeleri için kullanıldığını belirleme. Çekirdek veya standart düzenleyicilerini kullanabilir veya projeye özgü düzenleyiciler oluşturup kullanabilirsiniz. Daha fazla bilgi için bkz. [özel düzenleyiciler ve tasarımcılar oluşturma](../../extensibility/creating-custom-editors-and-designers.md) ve [nasıl yapılır: projeye özgü düzenleyiciler açma](../../extensibility/how-to-open-project-specific-editors.md).

3. Proje öğelerinizin **sınıf görünümü** ve **nesne tarayıcısı**sahip olacağı katılım düzeyini saptayın. Daha fazla bilgi için bkz. [support symbol-gözatma araçları](../../extensibility/internals/supporting-symbol-browsing-tools.md).

4. Daha önce projeniz ve proje öğeleriniz için yaptığınız tasarım kararlarını temel alarak yeni sınıflar türetirsiniz.

5. Aşağıdaki proje türü bileşenleri için kodu yazın:

    - Proje fabrikası, yeni proje oluşturmayı ve var olan projeleri açmayı yönetmek için. Daha fazla bilgi için bkz. [Proje fabrikalarını kullanarak proje örnekleri oluşturma](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).

    - Proje hiyerarşisi ve komut işleme. Daha fazla bilgi için bkz. [HierUtil7 proje sınıflarını kullanarak proje türü (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346), [proje modeli öğeleri](../../extensibility/internals/elements-of-a-project-model.md), [proje modeli çekirdek bileşenleri](../../extensibility/internals/project-model-core-components.md)ve [MenuCommands vs. OleMenuCommands](/visualstudio/misc/menucommands-vs-olemenucommands?view=vs-2015).

    - Proje öğeleri yönetimi, projenizi **Yeni proje** iletişim kutusuna ekleme da dahil. Daha fazla bilgi için bkz. [Proje ve proje öğesi şablonları ekleme](../../extensibility/internals/adding-project-and-project-item-templates.md) ve [Proje ve öğe şablonlarını kaydetme](../../extensibility/internals/registering-project-and-item-templates.md).

    - Proje durumunun ve bireysel öğelerinin kalıcılığı. Daha fazla bilgi için bkz. [Proje öğelerini açma ve kaydetme](../../extensibility/internals/opening-and-saving-project-items.md). Çözüm bilgilerinin sürekliliği için bkz. [çözümler](../../extensibility/internals/solutions-overview.md).

    - Özellikler penceresi görüntülenecek yapılandırmadan bağımsız Özellikler. Daha fazla bilgi için bkz. [özellikleri genişletme](../../extensibility/internals/extending-properties.md).

    - Yapılandırma bağımlı özellikleri göstermek için özellik sayfalarında uygulanan proje yapılandırma özellikleri. Daha fazla bilgi için bkz. [yapılandırma seçeneklerini yönetme](../../extensibility/internals/managing-configuration-options.md).

    - Dağıtım için çıktılar numaralandırılıyor. Daha fazla bilgi için bkz. [çıktı Için proje yapılandırması](../../extensibility/internals/project-configuration-for-output.md).

    - Project Başlangıç Hizmetleri. Daha fazla bilgi için bkz. [proje modeli](../../extensibility/internals/elements-of-a-project-model.md) ve [proje modeli çekirdek bileşenleri](../../extensibility/internals/project-model-core-components.md)öğeleri.

    - ' Den türetilmiş nesneler veya sınıflar `IDispatch` Otomasyon için kullanılabilir.

    - XML komut tablosu (*. vsct*) dosyaları. Daha fazla bilgi için bkz. [Visual Studio komut tablosu (. vsct) dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

6. Proje türünü test edin, hata ayıklayın ve başlatın.

7. Projeniz için değer olarak ayarlayarak **Başvuru Ekle** Iletişim kutusunun **Proje** sekmesinde projenizi görüntüleyin `VARIANT_TRUE` `VSHPROPID_ShowProjInSolutionPage` . Daha fazla bilgi için <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> bölümlerine bakın.

8. VSPackages 'yi yüklemek için Microsoft Installer (*. msi*) dosyasını oluşturun. Daha fazla bilgi için bkz. [Windows Installer Ile VSPackages](../../extensibility/internals/installing-vspackages-with-windows-installer.md)'yi, [bir proje türünü](../../extensibility/internals/registering-a-project-type.md)ve [VSPackages](../../extensibility/internals/vspackages.md)'yi kaydetme.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio’da Hiyerarşiler](../../extensibility/internals/hierarchies-in-visual-studio.md)
- [Proje türleri ne zaman oluşturulur](../../extensibility/internals/when-to-create-project-types.md)
- [Proje türleri oluştur](../../extensibility/internals/creating-project-types.md)
