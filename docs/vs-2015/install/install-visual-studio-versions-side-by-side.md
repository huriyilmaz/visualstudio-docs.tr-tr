---
title: Visual Studio sürümlerini yan yana yükler | Microsoft Docs
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
ms.openlocfilehash: 1ef2d51e35a198dbe6da3c1a034dd7c8d1bf8922
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851019"
---
# <a name="install-visual-studio-versions-side-by-side"></a>Visual Studio Sürümlerini Yan Yana Yükleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 'nun bu sürümünü, zaten daha önceki bir sürümün yüklü olduğu bir bilgisayara yükleyebilirsiniz. Yükleme sorunuyla karşılaşırsanız, hatalarda Hata ayıklayabilmeniz için hatalar hakkında bilgi toplamak üzere [günlük toplama aracını](https://www.microsoft.com/download/details.aspx?id=12493) kullanabilirsiniz.

> [!NOTE]
> [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Sürümlerini yayımlandıkları sırayla yüklemenizi öneririz. Örneğin, Visual Studio 2015 ' i yüklemeden önce Visual Studio 2013 ' yi yükleyebilirsiniz.

 Sürümleri yan yana yüklemeden önce aşağıdaki koşulları gözden geçirin:

- İçinde oluşturulan bir çözümü açmak için Visual Studio 2015 kullanıyorsanız [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] , Visual studio 2015 ' e özgü hiçbir özelliği uygulamadığınız sürece çözümü daha sonra eski sürümde açabilir ve değiştirebilirsiniz.

- Veya daha önceki bir sürümde oluşturulmuş bir çözümü açmak için Visual Studio 2015 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] ' i kullanmaya çalışırsanız, projelerinizi ve dosyalarınızı Visual studio 2015 ile uyumlu olacak şekilde değiştirmeniz gerekebilir. Daha fazla bilgi için bkz. [Visual Studio projelerini bağlantı noktası, geçirme ve yükseltme](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects?view=vs-2015) sayfası.

- Birden [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] fazla sürümü yüklü olan bir bilgisayarda sürümü kaldırırsanız, için dosya ilişkilendirmeleri [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] tüm sürümler için kaldırılır. Bu dosya ilişkilendirmelerini, [Seçenekler](../ide/reference/general-environment-options-dialog-box.md) Iletişim kutusunun **ortam**, **genel** sayfasındaki **dosya ilişkilendirmelerini geri yükle** düğmesini kullanarak yeniden eşleyebilirsiniz.

- Tüm uzantılar uyumlu olmadığından, Visual Studio uzantıları otomatik olarak yükseltmez. Uzantıları [Visual Studio Market](https://visualstudiogallery.msdn.microsoft.com/) veya yazılım yayımcısından yeniden yüklemeniz gerekir.

## <a name="net-framework-versions-and-side-by-side-installations"></a>.NET Framework sürümleri ve yan yana Yüklemeler

- Visual Basic, Visual C# ve Visual F# projeleri, projenin hangi .NET Framework sürümünü kullandığını belirtmek için **Proje tasarımcısında** **Target Framework** seçeneğini kullanır. Bir C++ projesi için. vcxproj dosyasını değiştirerek hedef çerçeveyi el ile değiştirebilirsiniz. Daha fazla bilgi için bkz. [sürüm uyumluluğu](https://msdn.microsoft.com/library/2f25e522-456a-48c3-8a53-e5f39275649f).

     Bir proje oluşturduğunuzda, **Yeni proje** iletişim kutusundaki **.NET Framework** listesinde projenin hangi .NET Framework sürümünü hedeflediğini belirtebilirsiniz.

     Dile özgü bilgiler için aşağıdaki tablodaki ilgili konuya bakın.

    |Dil|Konu|
    |--------------|-----------|
    |[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]|[Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)|
    |Visual C#|[Uygulama Sayfası, Proje Tasarımcısı (C#)](../ide/reference/application-page-project-designer-csharp.md)|
    |Visual F#|[Projeleri Yapılandırma](https://msdn.microsoft.com/library/a1489abb-6294-4f8f-b71f-2cb126393526)|
    |C++|[Nasıl yapılır: hedef Framework ve platform araç takımını değiştirme](https://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe)|
    |[!INCLUDE[jsprjscript](../includes/jsprjscript-md.md)]|[Bir JScript uygulamasını ortak dil çalışma zamanının önceki bir sürümünde çalıştırma](https://msdn.microsoft.com/bbea51b5-ac03-4e6c-b9a6-f487ef63eda5)|

## <a name="see-also"></a>Ayrıca Bkz.

- [Visual Studio'yu yükleme](../install/install-visual-studio-2015.md)
- [Visual Studio projelerini bağlantı noktası, geçirme ve yükseltme](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects?view=vs-2015)
- [C/C++ yalıtılmış uygulamaları ve yan yana derlemeler oluşturma](https://msdn.microsoft.com/library/9465904e-76f7-48bd-bb3f-c55d8f1699b6)
- [Visual Studio 'da geliştirme ayarlarını özelleştirme](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)
