---
title: Derleme Bilgileri İletişim Kutusu
description: derleme bilgileri iletişim kutusu ve .NET Framework genel derleme özniteliklerinin değerlerini belirtmek için nasıl kullanıldığı hakkında bilgi edinin.
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
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 70bd5357844dcfc9d58e09ae49cef6361b9fa995
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122151775"
---
# <a name="assembly-information-dialog-box"></a>Derleme Bilgileri iletişim kutusu

derleme bilgileri iletişim kutusu, projeniz ile otomatik olarak oluşturulan assemblyınfo dosyasında depolanan .NET Framework genel derleme özniteliklerinin değerlerini belirtmek için kullanılır. Çözüm Gezgini, assemblyınfo dosyası Visual Basic projeleri için **Project düğümmda** bulunur (görüntülemek için **tüm dosyaları göster** ' e tıklayın). C# projeleri için **Özellikler** altında bulunur. Daha fazla bilgi için bkz. [öznitelikler (C#)](/dotnet/csharp/programming-guide/concepts/attributes/index).

bu iletişim kutusuna erişmek için **Çözüm Gezgini**' de bir proje düğümü seçin ve sonra **Project** menüsünde **özellikler**' i seçin. **Uygulama** sayfasında, **derleme bilgileri** düğmesini seçin.

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
Derlemeyi tanımlayan benzersiz bir GUID. bir proje oluşturduğunuzda, Visual Studio derleme için bir guıd oluşturur. Öğesine karşılık gelir <xref:System.Guid> .

**Nötr dil**\
Derlemenin desteklediği kültürü belirtir. Öğesine karşılık gelir <xref:System.Resources.NeutralResourcesLanguageAttribute> . Varsayılan değer **(yok)**.

**Derlemeyi COM-görünür yap**\
Derlemedeki türlerin COM tarafından kullanılabilir olup olmayacağını belirtir. Öğesine karşılık gelir <xref:System.Runtime.InteropServices.ComVisibleAttribute> .

> [!NOTE]
> .NET Framework sınıf kitaplığında NuGet paketi oluştururken bu özellikleri ayarlama hakkında daha fazla bilgi için bkz. [paket için proje özelliklerini yapılandırma](/nuget/quickstart/create-and-publish-a-package-using-visual-studio-net-framework#configure-project-properties-for-the-package). lisanslama ve ifadeler hakkında bir NuGet paketiyle ilgili daha fazla bilgi için bkz. [licenses.nuget.org](/nuget/nuget-org/licenses.nuget.org/).

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)](../../ide/reference/application-page-project-designer-visual-basic.md)
- [Öznitelikler](/previous-versions/z0w1kczw(v=vs.140))