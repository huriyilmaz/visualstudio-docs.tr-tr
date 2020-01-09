---
title: Derleme Bilgileri İletişim Kutusu
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAssemblyInfo
helpviewer_keywords:
- Assembly Information dialog box
ms.assetid: 8f1f6449-e03d-4a5b-9076-d3b1f84ada48
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ae70a2bf989b73dedc5becaac6f4b49bd0108730
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595793"
---
# <a name="assembly-information-dialog-box"></a>Derleme Bilgileri iletişim kutusu

Derleme bilgileri iletişim kutusu, projeniz ile otomatik olarak oluşturulan AssemblyInfo dosyasında depolanan .NET Framework genel derleme özniteliklerinin değerlerini belirtmek için kullanılır. Çözüm Gezgini, AssemblyInfo dosyası, Visual Basic projeleri için **projem** düğümünden bulunur (görüntülemek için **tüm dosyaları göster** ' e tıklayın). Projeler C# için **Özellikler**altında bulunur. Daha fazla bilgi için bkz. [özniteliklerC#()](/dotnet/csharp/programming-guide/concepts/attributes/index).

Bu iletişim kutusuna erişmek için **Çözüm Gezgini**' de bir proje düğümü seçin ve ardından **Proje** menüsünde **Özellikler**' i seçin. **Uygulama** sayfasında, **derleme bilgileri** düğmesini seçin.

## <a name="uielement-list"></a>UIElement listesi

**Başlık**\
Bütünleştirilmiş kod bildirimi için bir başlık belirtir. <xref:System.Reflection.AssemblyTitleAttribute>karşılık gelir.

**Açıklama**\
Derleme bildirimi için isteğe bağlı bir açıklama belirtir. <xref:System.Reflection.AssemblyDescriptionAttribute>karşılık gelir.

**Şirket**\
Bütünleştirilmiş kod bildirimi için bir şirket adı belirtir. <xref:System.Reflection.AssemblyCompanyAttribute>karşılık gelir.

Şirket için varsayılan değeri kayıt defterinde ayarlayabilir veya değiştirebilirsiniz. Windows sürümünüze bağlı olarak, **\ HKEY_LOCAL_MACHINE \SOFTWARE\WOW6432Node\Microsoft\Windows NT\CurrentVersion** veya **Computer \ HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Windows Nt\currentversion** anahtarındaki **RegisteredOrganization** değerini arayın.

**Ürün**\
Derleme bildirimi için bir ürün adı belirtir. <xref:System.Reflection.AssemblyProductAttribute>karşılık gelir.

**Telif hakkı**\
Derleme bildirimi için bir telif hakkı bildirimi belirtir. <xref:System.Reflection.AssemblyCopyrightAttribute>karşılık gelir.

**Ticari marka**\
Derleme bildirimi için bir ticari marka belirtir. <xref:System.Reflection.AssemblyTrademarkAttribute>karşılık gelir.

**Derleme sürümü**\
Derlemenin sürümünü belirtir. <xref:System.Reflection.AssemblyVersionAttribute>karşılık gelir.

**Dosya sürümü**\
Derleyiciye Win32 dosya sürümü kaynağı için belirli bir sürüm kullanmasını yönlendiren bir sürüm numarası belirtir. <xref:System.Reflection.AssemblyFileVersionAttribute>karşılık gelir.

**Guıd**\
Derlemeyi tanımlayan benzersiz bir GUID. Bir proje oluşturduğunuzda, Visual Studio derleme için bir GUID oluşturur. <xref:System.Guid>karşılık gelir.

**Nötr dil**\
Derlemenin desteklediği kültürü belirtir. <xref:System.Resources.NeutralResourcesLanguageAttribute>karşılık gelir. Varsayılan değer **(yok)** .

**DERLEMEYI com görünebilir yapın**\
Derlemedeki türlerin COM tarafından kullanılabilir olup olmayacağını belirtir. <xref:System.Runtime.InteropServices.ComVisibleAttribute>karşılık gelir.

> [!NOTE]
> Bir .NET Framework sınıf kitaplığında bir NuGet paketi oluştururken bu özellikleri ayarlama hakkında daha fazla bilgi için bkz. [paket için proje özelliklerini yapılandırma](/nuget/quickstart/create-and-publish-a-package-using-visual-studio-net-framework#configure-project-properties-for-the-package).

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)](../../ide/reference/application-page-project-designer-visual-basic.md)
- [Öznitelikler](https://msdn.microsoft.com/Library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)
