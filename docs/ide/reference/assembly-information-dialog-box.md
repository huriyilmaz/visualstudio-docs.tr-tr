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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595793"
---
# <a name="assembly-information-dialog-box"></a>Derleme Bilgileri iletişim kutusu

Derleme Bilgileri iletişim kutusu, .NET Framework global derleme özniteliklerinin, projenizle otomatik olarak oluşturulan AssemblyInfo dosyasında depolanan değerlerini belirtmek için kullanılır. Solution Explorer'da, AssemblyInfo dosyası Visual Basic projeleri için **Projem** düğümünde bulunur (görüntülemek için **Tüm dosyaları göster'i** tıklatın). C# projeleri için **Özellikler**altında yer alır. Daha fazla bilgi için [Öznitelikler (C#)](/dotnet/csharp/programming-guide/concepts/attributes/index)'ye bakın.

Bu iletişim kutusuna erişmek için Çözüm **Gezgini'nde**bir proje düğümü seçin ve ardından **Proje** menüsünde **Özellikler'i**seçin. **Uygulama** **sayfasında, Montaj Bilgileri** düğmesini seçin.

## <a name="uielement-list"></a>UIElement listesi

**Başlık**\
Derleme bildirimi için bir başlık belirtir. Karşılık <xref:System.Reflection.AssemblyTitleAttribute>gelir.

**Açıklama**\
Derleme bildirimi için isteğe bağlı bir açıklama belirtir. Karşılık <xref:System.Reflection.AssemblyDescriptionAttribute>gelir.

**Şirket**\
Montaj bildirimi için bir şirket adı belirtir. Karşılık <xref:System.Reflection.AssemblyCompanyAttribute>gelir.

Kayıt defterinde Şirket için varsayılan değeri ayarlayabilir veya değiştirebilirsiniz. Windows sürümünüze bağlı olarak **Bilgisayar\HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Windows NT\CurrentVersion** veya **Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion** tuşu altında **Kayıtlı Kuruluş** değerini arayın.

**Ürün**\
Montaj bildirimi için bir ürün adı belirtir. Karşılık <xref:System.Reflection.AssemblyProductAttribute>gelir.

**Telif hakkı**\
Derleme bildirimi için bir telif hakkı bildirimi belirtir. Karşılık <xref:System.Reflection.AssemblyCopyrightAttribute>gelir.

**Marka**\
Derleme manifestosu için bir ticari marka belirtir. Karşılık <xref:System.Reflection.AssemblyTrademarkAttribute>gelir.

**Montaj Sürümü**\
Derlemenin sürümünü belirtir. Karşılık <xref:System.Reflection.AssemblyVersionAttribute>gelir.

**Dosya Sürümü**\
Derleyiciye Win32 dosya sürümü kaynağı için belirli bir sürümü kullanmasını söyleyen bir sürüm numarası belirtir. Karşılık <xref:System.Reflection.AssemblyFileVersionAttribute>gelir.

**Guıd**\
Derlemeyi tanımlayan benzersiz bir GUID. Bir proje oluşturduğunuzda, Visual Studio derleme için bir GUID oluşturur. Karşılık <xref:System.Guid>gelir.

**Tarafsız Dil**\
Derlemenin hangi kültürü desteklediğini belirtir. Karşılık <xref:System.Resources.NeutralResourcesLanguageAttribute>gelir. Varsayılan **değer (Yok)** olur.

**DerlemeYI COM-Görünür yapma**\
Derlemedeki türlerin COM için kullanılabilir olup olmayacağını belirtir. Karşılık <xref:System.Runtime.InteropServices.ComVisibleAttribute>gelir.

> [!NOTE]
> .NET Framework sınıf kitaplığında bir NuGet paketi oluştururken bu özellikleri ayarlama hakkında daha fazla bilgi [için](/nuget/quickstart/create-and-publish-a-package-using-visual-studio-net-framework#configure-project-properties-for-the-package)bkz.

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)](../../ide/reference/application-page-project-designer-visual-basic.md)
- [Öznitelikler](https://msdn.microsoft.com/Library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)
