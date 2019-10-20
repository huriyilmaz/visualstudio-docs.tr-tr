---
title: Derleme Bilgileri İletişim Kutusu
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAssemblyInfo
helpviewer_keywords:
- Assembly Information dialog box
ms.assetid: 8f1f6449-e03d-4a5b-9076-d3b1f84ada48
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 88d86c077cf129632c78d6266e7c8146325b78fb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651913"
---
# <a name="assembly-information-dialog-box"></a>Derleme Bilgileri iletişim kutusu

Derleme bilgileri iletişim kutusu, projeniz ile otomatik olarak oluşturulan AssemblyInfo dosyasında depolanan .NET Framework genel derleme özniteliklerinin değerlerini belirtmek için kullanılır. Çözüm Gezgini, AssemblyInfo dosyası, Visual Basic projeleri için **projem** düğümünden bulunur (görüntülemek için **tüm dosyaları göster** ' e tıklayın). Projeler C# için **Özellikler**altında bulunur. Daha fazla bilgi için bkz. [özniteliklerC#()](/dotnet/csharp/programming-guide/concepts/attributes/index).

Bu iletişim kutusuna erişmek için **Çözüm Gezgini**' de bir proje düğümü seçin ve ardından **Proje** menüsünde **Özellikler**' i seçin. **Uygulama** sayfasında, **derleme bilgileri** düğmesini seçin.

## <a name="uielement-list"></a>UIElement listesi

**Başlık** \
Bütünleştirilmiş kod bildirimi için bir başlık belirtir. @No__t_0 karşılık gelir.

**Açıklama** \
Derleme bildirimi için isteğe bağlı bir açıklama belirtir. @No__t_0 karşılık gelir.

**Şirket** \
Bütünleştirilmiş kod bildirimi için bir şirket adı belirtir. @No__t_0 karşılık gelir.

Şirket için varsayılan değeri kayıt defterinde ayarlayabilir veya değiştirebilirsiniz. **Computer\hkey_local_machıne\software\wow6432node\microsoft\windows NT\CurrentVersion** veya **computer\hkey_local_machıne\software\microsoft\windows NT\CurrentVersion altındaki RegisteredOrganization değerini arayın** anahtar, Windows sürümünüze bağlı olarak.

**Ürün** \
Derleme bildirimi için bir ürün adı belirtir. @No__t_0 karşılık gelir.

**Telif hakkı** \
Derleme bildirimi için bir telif hakkı bildirimi belirtir. @No__t_0 karşılık gelir.

**Ticari marka** \
Derleme bildirimi için bir ticari marka belirtir. @No__t_0 karşılık gelir.

**Derleme sürümü** \
Derlemenin sürümünü belirtir. @No__t_0 karşılık gelir.

**Dosya sürümü** \
Derleyiciye Win32 dosya sürümü kaynağı için belirli bir sürüm kullanmasını yönlendiren bir sürüm numarası belirtir. @No__t_0 karşılık gelir.

**Guıd** \
Derlemeyi tanımlayan benzersiz bir GUID. Bir proje oluşturduğunuzda, Visual Studio derleme için bir GUID oluşturur. @No__t_0 karşılık gelir.

**Nötr dil** \
Derlemenin desteklediği kültürü belirtir. @No__t_0 karşılık gelir. Varsayılan değer **(yok)** .

**DERLEMEYI com görünebilir yapın** \
Derlemedeki türlerin COM tarafından kullanılabilir olup olmayacağını belirtir. @No__t_0 karşılık gelir.

> [!NOTE]
> Bir .NET Framework sınıf kitaplığında bir NuGet paketi oluştururken bu özellikleri ayarlama hakkında daha fazla bilgi için bkz. [paket için proje özelliklerini yapılandırma](/nuget/quickstart/create-and-publish-a-package-using-visual-studio-net-framework#configure-project-properties-for-the-package).

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)](../../ide/reference/application-page-project-designer-visual-basic.md)
- [Öznitelikler](https://msdn.microsoft.com/Library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)
