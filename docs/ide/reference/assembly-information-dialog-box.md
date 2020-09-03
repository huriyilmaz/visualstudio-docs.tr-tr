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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75595793"
---
# <a name="assembly-information-dialog-box"></a>Derleme Bilgileri iletişim kutusu

Derleme bilgileri iletişim kutusu, projeniz ile otomatik olarak oluşturulan AssemblyInfo dosyasında depolanan .NET Framework genel derleme özniteliklerinin değerlerini belirtmek için kullanılır. Çözüm Gezgini, AssemblyInfo dosyası, Visual Basic projeleri için **projem** düğümünden bulunur (görüntülemek için **tüm dosyaları göster** ' e tıklayın). C# projeleri için **Özellikler**altında bulunur. Daha fazla bilgi için bkz. [öznitelikler (C#)](/dotnet/csharp/programming-guide/concepts/attributes/index).

Bu iletişim kutusuna erişmek için **Çözüm Gezgini**' de bir proje düğümü seçin ve ardından **Proje** menüsünde **Özellikler**' i seçin. **Uygulama** sayfasında, **derleme bilgileri** düğmesini seçin.

## <a name="uielement-list"></a>UIElement listesi

**Başlığın**\
Bütünleştirilmiş kod bildirimi için bir başlık belirtir. Öğesine karşılık gelir <xref:System.Reflection.AssemblyTitleAttribute> .

**Açıklaması**\
Derleme bildirimi için isteğe bağlı bir açıklama belirtir. Öğesine karşılık gelir <xref:System.Reflection.AssemblyDescriptionAttribute> .

**Şirketlerin**\
Bütünleştirilmiş kod bildirimi için bir şirket adı belirtir. Öğesine karşılık gelir <xref:System.Reflection.AssemblyCompanyAttribute> .

Şirket için varsayılan değeri kayıt defterinde ayarlayabilir veya değiştirebilirsiniz. Windows sürümünüze bağlı olarak, **\ HKEY_LOCAL_MACHINE \SOFTWARE\WOW6432Node\Microsoft\Windows NT\CurrentVersion** veya **Computer \ HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Windows Nt\currentversion** anahtarındaki **RegisteredOrganization** değerini arayın.

**Ürünüyle**\
Derleme bildirimi için bir ürün adı belirtir. Öğesine karşılık gelir <xref:System.Reflection.AssemblyProductAttribute> .

**Yaptırımlar**\
Derleme bildirimi için bir telif hakkı bildirimi belirtir. Öğesine karşılık gelir <xref:System.Reflection.AssemblyCopyrightAttribute> .

**Dır**\
Derleme bildirimi için bir ticari marka belirtir. Öğesine karşılık gelir <xref:System.Reflection.AssemblyTrademarkAttribute> .

**Derleme sürümü**\
Derlemenin sürümünü belirtir. Öğesine karşılık gelir <xref:System.Reflection.AssemblyVersionAttribute> .

**Dosya sürümü**\
Derleyiciye Win32 dosya sürümü kaynağı için belirli bir sürüm kullanmasını yönlendiren bir sürüm numarası belirtir. Öğesine karşılık gelir <xref:System.Reflection.AssemblyFileVersionAttribute> .

**'INI**\
Derlemeyi tanımlayan benzersiz bir GUID. Bir proje oluşturduğunuzda, Visual Studio derleme için bir GUID oluşturur. Öğesine karşılık gelir <xref:System.Guid> .

**Nötr dil**\
Derlemenin desteklediği kültürü belirtir. Öğesine karşılık gelir <xref:System.Resources.NeutralResourcesLanguageAttribute> . Varsayılan değer **(yok)**.

**Derlemeyi COM-görünür yap**\
Derlemedeki türlerin COM tarafından kullanılabilir olup olmayacağını belirtir. Öğesine karşılık gelir <xref:System.Runtime.InteropServices.ComVisibleAttribute> .

> [!NOTE]
> Bir .NET Framework sınıf kitaplığında bir NuGet paketi oluştururken bu özellikleri ayarlama hakkında daha fazla bilgi için bkz. [paket için proje özelliklerini yapılandırma](/nuget/quickstart/create-and-publish-a-package-using-visual-studio-net-framework#configure-project-properties-for-the-package).

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)](../../ide/reference/application-page-project-designer-visual-basic.md)
- [Öznitelikler](https://msdn.microsoft.com/Library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)
