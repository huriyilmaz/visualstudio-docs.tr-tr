---
title: 'denetim listesi: yeni Project türleri oluşturma | Microsoft Docs'
description: Visual Studio yeni bir proje türü oluşturmak ve göstermek için tamamlanması gereken görevler hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating new types
- project types, checklist for creating
ms.assetid: 29eb9c3b-1933-4741-aa85-65a33f0825ba
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 302ec482e15b837a8287520170c40e2765f0d09b5693028a132f6af063c8030e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121359747"
---
# <a name="checklist-create-new-project-types"></a>Denetim listesi: yeni proje türleri oluşturma
Yeni bir proje türü oluşturmak için birkaç görevi gerçekleştirmeniz gerekir. Aşağıdaki denetim listesi, bu görevlere rehberlik sağlar:

1. Yeni proje türü için işlevselliği tasarlayın. daha fazla bilgi için bkz. [Project türü tasarım kararları](../../extensibility/internals/project-type-design-decisions.md).

2. Hangi düzenleyicilerin kod ve diğer proje öğeleri için kullanıldığını belirleme. Çekirdek veya standart düzenleyicilerini kullanabilir veya projeye özgü düzenleyiciler oluşturup kullanabilirsiniz. Daha fazla bilgi için bkz. [özel düzenleyiciler ve tasarımcılar oluşturma](../../extensibility/creating-custom-editors-and-designers.md) ve [nasıl yapılır: projeye özgü düzenleyiciler açma](../../extensibility/how-to-open-project-specific-editors.md).

3. Proje öğelerinizin **sınıf görünümü** ve **nesne tarayıcısı** sahip olacağı katılım düzeyini saptayın. Daha fazla bilgi için bkz. [support symbol-gözatma araçları](../../extensibility/internals/supporting-symbol-browsing-tools.md).

4. Daha önce projeniz ve proje öğeleriniz için yaptığınız tasarım kararlarını temel alarak yeni sınıflar türetirsiniz.

5. Aşağıdaki proje türü bileşenleri için kodu yazın:

    - yeni proje oluşturmayı ve var olan projeleri açmayı yönetmek için Project fabrikası. Daha fazla bilgi için bkz. [Proje fabrikalarını kullanarak proje örnekleri oluşturma](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).

    - hiyerarşi ve komut işleme Project. daha fazla bilgi için bkz. [HierUtil7 proje sınıflarını kullanarak proje türü (C++)](/previous-versions/bb166212(v=vs.100)), [proje modeli öğeleri](../../extensibility/internals/elements-of-a-project-model.md), [Project model çekirdek bileşenleri](../../extensibility/internals/project-model-core-components.md)ve [menucommands vs. olemenucommands](/previous-versions/visualstudio/visual-studio-2015/misc/menucommands-vs-olemenucommands?preserve-view=true&view=vs-2015).

    - **yeni Project** iletişim kutusuna projenizi ekleme dahil olmak üzere Project öğeleri yönetimi. Daha fazla bilgi için bkz. [Proje ve proje öğesi şablonları ekleme](../../extensibility/internals/adding-project-and-project-item-templates.md) ve [Proje ve öğe şablonlarını kaydetme](../../extensibility/internals/registering-project-and-item-templates.md).

    - Proje durumunun ve bireysel öğelerinin kalıcılığı. Daha fazla bilgi için bkz. [Proje öğelerini açma ve kaydetme](../../extensibility/internals/opening-and-saving-project-items.md). Çözüm bilgilerinin sürekliliği için bkz. [çözümler](../../extensibility/internals/solutions-overview.md).

    - Özellikler penceresi görüntülenecek yapılandırmadan bağımsız Özellikler. Daha fazla bilgi için bkz. [özellikleri genişletme](../../extensibility/internals/extending-properties.md).

    - yapılandırmaya bağlı özellikleri göstermek için özellik sayfalarında uygulanan yapılandırma özelliklerini Project. Daha fazla bilgi için bkz. [yapılandırma seçeneklerini yönetme](../../extensibility/internals/managing-configuration-options.md).

    - Dağıtım için çıktılar numaralandırılıyor. daha fazla bilgi için bkz. [çıkış için Project yapılandırması](../../extensibility/internals/project-configuration-for-output.md).

    - Project başlangıç hizmetleri. daha fazla bilgi için bkz. [proje modeli](../../extensibility/internals/elements-of-a-project-model.md) ve [Project modeli çekirdek bileşenleri](../../extensibility/internals/project-model-core-components.md)öğeleri.

    - ' Den türetilmiş nesneler veya sınıflar `IDispatch` Otomasyon için kullanılabilir.

    - XML komut tablosu (*. vsct*) dosyaları. daha fazla bilgi için bkz. [Visual Studio komut tablosu (. vsct) dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

6. Proje türünü test edin, hata ayıklayın ve başlatın.

7. projeniz için değer olarak ayarlayarak **başvuru ekle** iletişim kutusunun **Project** sekmesinde projenizi görüntüleyin `VARIANT_TRUE` `VSHPROPID_ShowProjInSolutionPage` . Daha fazla bilgi için <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> bölümlerine bakın.

8. VSPackages 'yi yüklemek için Microsoft Installer (*.msi*) dosyasını oluşturun. daha fazla bilgi için bkz. [Windows Installer ile vspackages](../../extensibility/internals/installing-vspackages-with-windows-installer.md)'yi, [bir proje türünü](../../extensibility/internals/registering-a-project-type.md)ve [vspackages](../../extensibility/internals/vspackages.md)'yi kaydetme.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio’da Hiyerarşiler](../../extensibility/internals/hierarchies-in-visual-studio.md)
- [Proje türleri ne zaman oluşturulur](../../extensibility/internals/when-to-create-project-types.md)
- [Proje türleri oluştur](../../extensibility/internals/creating-project-types.md)