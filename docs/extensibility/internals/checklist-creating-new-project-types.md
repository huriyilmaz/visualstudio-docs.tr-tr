---
title: 'Denetim Listesi: Yeni Project Türleri | Microsoft Docs'
description: Yeni proje türünü oluşturmak ve görüntülemek için tamamlanması gereken görevler hakkında bilgi Visual Studio.
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
ms.openlocfilehash: e7cb031b55a83dbc2694b8532c91b013a343ffa3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122124795"
---
# <a name="checklist-create-new-project-types"></a>Denetim listesi: Yeni proje türleri oluşturma
Yeni bir proje türü oluşturmak için birkaç görevi tamamlamanız gerekir. Aşağıdaki denetim listesi bu görevler için bir kılavuz sağlar:

1. Yeni proje türünüz için işlevselliği tasarlar. Daha fazla bilgi için [bkz. Project tasarım kararlarını alma.](../../extensibility/internals/project-type-design-decisions.md)

2. Kod ve diğer proje öğeleri için kullanılan düzenleyicileri belirleme. Çekirdek veya standart düzenleyicileri kullanabilir veya projeye özgü düzenleyiciler oluşturabilir ve kullanabilirsiniz. Daha fazla bilgi için, [bkz. Create custom editors and designers](../../extensibility/creating-custom-editors-and-designers.md) and [How to: Open project-specific editors](../../extensibility/how-to-open-project-specific-editors.md).

3. Proje öğelerinizin nesnesinde ve Object **Browser'da Sınıf Görünümü** **katılım düzeyini belirleme.** Daha fazla bilgi için [bkz. Sembol tarama araçlarını destekleme.](../../extensibility/internals/supporting-symbol-browsing-tools.md)

4. Projeniz ve proje öğeleriniz için daha önce aldığı tasarım kararlarına göre yeni sınıflar türetin.

5. Aşağıdaki proje türü bileşenleri için kodu yazın:

    - Project proje oluşturmayı ve mevcut projeleri açmayı yönetmek için bir fabrika oluşturabilirsiniz. Daha fazla bilgi için [bkz. Proje fabrikalarını kullanarak proje örnekleri oluşturma.](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)

    - Project hiyerarşi ve komut işleme. Daha fazla bilgi için bkz. Proje türü (C++) uygulamak için [HierUtil7](/previous-versions/bb166212(v=vs.100))proje sınıflarını [kullanma,](../../extensibility/internals/elements-of-a-project-model.md)proje modelinin öğeleri, [Project model](../../extensibility/internals/project-model-core-components.md)çekirdek bileşenleri ve [MenuCommands ile OleMenuCommands karşılaştırması.](/previous-versions/visualstudio/visual-studio-2015/misc/menucommands-vs-olemenucommands?preserve-view=true&view=vs-2015)

    - Project yeni öğeler iletişim kutusuna eklemek de dahil olmak üzere **Project** yönetimi. Daha fazla bilgi için [bkz. Proje ve proje öğesi şablonları ekleme ve](../../extensibility/internals/adding-project-and-project-item-templates.md) Proje ve öğe [şablonlarını kaydetme.](../../extensibility/internals/registering-project-and-item-templates.md)

    - Proje durumunun ve tek tek öğelerin kalıcılığı. Daha fazla bilgi için [bkz. Proje öğelerini açma ve kaydetme.](../../extensibility/internals/opening-and-saving-project-items.md) Çözüm bilgileri kalıcılığı için bkz. [Çözümler.](../../extensibility/internals/solutions-overview.md)

    - Yapılandırmadan bağımsız özellikler, Özellikler penceresi. Daha fazla bilgi için [bkz. Özellikleri genişletme.](../../extensibility/internals/extending-properties.md)

    - Project özellikleri göstermek için özellik sayfalarında uygulanan yapılandırma özelliklerini kullanın. Daha fazla bilgi için [bkz. Yapılandırma seçeneklerini yönetme.](../../extensibility/internals/managing-configuration-options.md)

    - Dağıtım için çıkışları numaralar. Daha fazla bilgi için [bkz. Project için yapılandırmayı yapılandırma.](../../extensibility/internals/project-configuration-for-output.md)

    - Project hizmetleri. Daha fazla bilgi için [bkz. Proje modelinin öğeleri](../../extensibility/internals/elements-of-a-project-model.md) ve [Project temel bileşenleri.](../../extensibility/internals/project-model-core-components.md)

    - nesnesinden türetilen nesneler veya sınıflar `IDispatch` otomasyon için kullanılabilir.

    - XML komut tablosu (*.vsct*) dosyaları. Daha fazla bilgi için [bkz. Visual Studio tablosu (.vsct) dosyaları.](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

6. Proje türlerinizi test etmek, hata ayıklamak ve başlatmak.

7. Projenizi Başvuru **Project** iletişim **kutusunun** Giriş sekmesinde değeri olarak `VARIANT_TRUE` ayarerek `VSHPROPID_ShowProjInSolutionPage` görüntüleyin. Daha fazla bilgi için <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> bölümlerine bakın.

8. VSPackage'larınızı *yüklemek için Microsoft* Installer (.msi) dosyasını oluşturun. Daha fazla bilgi için [bkz. Windows Yükleyicisi ile VSPackage'ları Yükleme,](../../extensibility/internals/installing-vspackages-with-windows-installer.md)Proje türünü [kaydetme](../../extensibility/internals/registering-a-project-type.md)ve [VSPackages.](../../extensibility/internals/vspackages.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio’da Hiyerarşiler](../../extensibility/internals/hierarchies-in-visual-studio.md)
- [Proje türleri ne zaman oluşturularak oluşturularak](../../extensibility/internals/when-to-create-project-types.md)
- [Proje türleri oluşturma](../../extensibility/internals/creating-project-types.md)