---
title: Visual Studio sürümlerini yan yana yükleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
helpviewer_keywords:
- side-by-side installations [Visual Studio]
- Help [Visual Studio], installing
- install multiple versions of Visual Studio
ms.assetid: 4d00f240-4910-4699-aaf3-cda6461f0c29
caps.latest.revision: 48
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: a146872561c4be5fe48016c17eb64ad6f854106a
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298028"
---
# <a name="install-visual-studio-versions-side-by-side"></a>Visual Studio sürümlerini yan yana yükleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio'nun bu sürümü zaten daha önceki bir sürümün yüklü olduğu bir bilgisayara yükleyebilirsiniz. Yükleme sorunuyla karşılaşırsanız, hatalarda Hata ayıklayabilmeniz için hatalar hakkında bilgi toplamak üzere [günlük toplama aracını](https://go.microsoft.com/fwlink/?LinkId=262077) kullanabilirsiniz.

> [!NOTE]
> [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sürümlerini yayımlandıkları sırayla yüklemenizi öneririz. Örneğin, Visual Studio 2015'i yüklemeden önce Visual Studio 2013 yükleyin.

 Sürümleri yan yana yüklemeden önce aşağıdaki koşulları gözden geçirin:

- [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]' de oluşturulmuş bir çözümü açmak için Visual Studio 2015 kullanıyorsanız, Visual Studio 2015 ' e özgü herhangi bir özelliği uygulamadıysanız daha sonra çözümü daha sonra eski sürümde açabilir ve değiştirebilirsiniz.

- [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] veya önceki bir sürümde oluşturulmuş bir çözümü açmak için Visual Studio 2015 ' i kullanmaya çalışırsanız, projelerinizi ve dosyalarınızı Visual Studio 2015 ile uyumlu olacak şekilde değiştirmeniz gerekebilir. Daha fazla bilgi için bkz. [Visual Studio projelerini bağlantı noktası, geçirme ve yükseltme](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects?view=vs-2015) sayfası.

- Birden fazla sürümü yüklü olan bir bilgisayarda [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sürümünü kaldırırsanız, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] için dosya ilişkilendirmeleri tüm sürümler için kaldırılır. Bu dosya ilişkilendirmelerini, [Seçenekler](../ide/reference/general-environment-options-dialog-box.md) Iletişim kutusunun **ortam**, **genel** sayfasındaki **dosya ilişkilendirmelerini geri yükle** düğmesini kullanarak yeniden eşleyebilirsiniz.

- Tüm uzantıları uyumlu olmadığından visual Studio uzantıları otomatik olarak yükseltmez. Uzantıları [Visual Studio Market](https://go.microsoft.com/fwlink/?LinkId=178891) veya yazılım yayımcısından yeniden yüklemeniz gerekir.

## <a name="net-framework-versions-and-side-by-side-installations"></a>.NET framework sürümleri ve yan yana yüklemeler

- Visual Basic, görsel C#ve görsel F# projeler, projenin hangi .NET Framework sürümünü kullandığını belirtmek Için **Proje tasarımcısında** **Target Framework** seçeneğini kullanır. Bir C++ projesi için .vcxproj dosyasını değiştirerek hedef Framework'ü el ile değiştirebilirsiniz. Daha fazla bilgi için bkz. [sürüm uyumluluğu](https://msdn.microsoft.com/library/2f25e522-456a-48c3-8a53-e5f39275649f).

     Bir proje oluşturduğunuzda, **Yeni proje** iletişim kutusundaki **.NET Framework** listesinde projenin hangi .NET Framework sürümünü hedeflediğini belirtebilirsiniz.

     Dile özgü bilgiler için aşağıdaki tabloda ilgili konuya bakın.

    |Dil|Konu|
    |--------------|-----------|
    |[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]|[Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)|
    |Visual C#|[Uygulama Sayfası, Proje Tasarımcısı (C#)](../ide/reference/application-page-project-designer-csharp.md)|
    |Visual F#|[Projeleri Yapılandırma](https://msdn.microsoft.com/library/a1489abb-6294-4f8f-b71f-2cb126393526)|
    |C++|[Nasıl Yapılır: Hedef Framework ve Platform Araç Kümesini Değiştirme](https://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe)|
    |[!INCLUDE[jsprjscript](../includes/jsprjscript-md.md)]|[Bir JScript uygulamasını ortak dil çalışma zamanının önceki bir sürümünde çalıştırma](https://msdn.microsoft.com/bbea51b5-ac03-4e6c-b9a6-f487ef63eda5)|

## <a name="see-also"></a>Ayrıca Bkz.

- [Visual Studio'yu yükleyin](../install/install-visual-studio-2015.md)
- [Visual Studio projelerini bağlantı noktası, geçirme ve yükseltme](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects?view=vs-2015)
- [C/C++ Yalıtılmış Uygulamaları ve Yan Yana Derlemeleri Oluşturma](https://msdn.microsoft.com/library/9465904e-76f7-48bd-bb3f-c55d8f1699b6)
- [Visual Studio 'da geliştirme ayarlarını özelleştirme](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)