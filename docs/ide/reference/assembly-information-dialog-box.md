---
title: Derleme Bilgileri İletişim Kutusu
description: Derleme bilgileri iletişim kutusu ve .NET Framework genel derleme özniteliklerinin değerlerini belirtmek için nasıl kullanıldığı hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAssemblyInfo
helpviewer_keywords:
- Assembly Information dialog box
ms.assetid: 8f1f6449-e03d-4a5b-9076-d3b1f84ada48
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0a8f4d5612fe8ceaa4470f441133767178b119cc
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2021
ms.locfileid: "107295448"
---
# <a name="assembly-information-dialog-box"></a>Derleme Bilgileri iletişim kutusu

Derleme bilgileri iletişim kutusu, projeniz ile otomatik olarak oluşturulan AssemblyInfo dosyasında depolanan .NET Framework genel derleme özniteliklerinin değerlerini belirtmek için kullanılır. Çözüm Gezgini, AssemblyInfo dosyası, Visual Basic projeleri için **projem** düğümünden bulunur (görüntülemek için **tüm dosyaları göster** ' e tıklayın). C# projeleri için **Özellikler** altında bulunur. Daha fazla bilgi için bkz. [öznitelikler (C#)](/dotnet/csharp/programming-guide/concepts/attributes/index).

Bu iletişim kutusuna erişmek için **Çözüm Gezgini**' de bir proje düğümü seçin ve ardından **Proje** menüsünde **Özellikler**' i seçin. **Uygulama** sayfasında, **derleme bilgileri** düğmesini seçin.

## <a name="uielement-list"></a>UIElement listesi

**Başlığın**\
Bütünleştirilmiş kod bildirimi için bir başlık belirtir. Öğesine karşılık gelir <xref:System.Reflection.AssemblyTitleAttribute> .

**Açıklaması**\
Derleme bildirimi için isteğe bağlı bir açıklama belirtir. Öğesine karşılık gelir <xref:System.Reflection.AssemblyDescriptionAttribute> .

**Şirketlerin**\
Bütünleştirilmiş kod bildirimi için bir şirket adı belirtir. Öğesine karşılık gelir <xref:System.Reflection.AssemblyCompanyAttribute> .

Şirket için varsayılan değeri kayıt defterinde ayarlayabilir veya değiştirebilirsiniz. Windows sürümünüze bağlı olarak **Computer\HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Windows NT\CurrentVersion** veya **Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion** anahtarı altında **RegisteredOrganization** değerini arayın.

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
> Bir .NET Framework sınıf kitaplığında bir NuGet paketi oluştururken bu özellikleri ayarlama hakkında daha fazla bilgi için bkz. [paket için proje özelliklerini yapılandırma](/nuget/quickstart/create-and-publish-a-package-using-visual-studio-net-framework#configure-project-properties-for-the-package). Ayrıca, bir NuGet paketiyle ilgili olarak lisanslama ve Ifadeler hakkında daha fazla bilgi için bkz. [Licenses.NuGet.org](/nuget/nuget-org/licenses.nuget.org/).

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)](../../ide/reference/application-page-project-designer-visual-basic.md)
- [Öznitelikler](/previous-versions/z0w1kczw(v=vs.140))