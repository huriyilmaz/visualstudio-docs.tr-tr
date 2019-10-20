---
title: Kaynak olarak meta veriler | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- Go To Definition command
- Code Definition window, viewing metadata as source
- metadata as source [C#]
ms.assetid: 4945a07f-b3be-4f05-a587-fc29058aa8fa
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b1d96224be13a12dcaadb394584f8441c7bd1934
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667517"
---
# <a name="metadata-as-source"></a>Kaynak olarak Meta Veriler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kaynak olarak meta veriler, salt okunurdur bir arabellekte kaynak kodu C# olarak görünen meta verileri görüntülemenize olanak sağlar. Bu, türlerin ve üyelerin bildirimlerinin (uygulamalar olmadan) bir görünümünü sunar. Kaynak kodu proje veya çözümünüz tarafından kullanılamayan türler veya Üyeler için **Tanıma Git** komutunu çalıştırarak meta verileri kaynak olarak görüntüleyebilirsiniz.

> [!NOTE]
> İç olarak işaretlenmiş türler veya Üyeler için **tanım gönder** komutunu çalıştırmayı denediğinizde, tümleşik geliştirme ORTAMı (IDE), başvuran derlemenin arkadaş olup olmamasına bakılmaksızın meta verilerini kaynak olarak görüntülemez.

 Meta verileri kod düzenleyicisinde ya da **kod tanımı** penceresinde kaynak olarak görüntüleyebilirsiniz.

## <a name="viewing-metadata-as-source-in-the-code-editor"></a>Meta verileri kod düzenleyicisinde kaynak olarak görüntüleme
 Kaynak kodu kullanılamayan bir öğe için **Tanıma Git** komutunu çalıştırdığınızda, kod Düzenleyicisi 'nde, kaynak olarak görüntülenen bu öğenin meta verilerinin görünümünü içeren sekmeli bir belge görüntülenir. Türün adı, ardından **gelen [meta verilerden]** belge sekmesinde görünür.

 Örneğin, <xref:System.Console> için **tanımına git** komutunu çalıştırırsanız, <xref:System.Console> meta verileri kod düzenleyicisinde bildirimine benzer ancak bir uygulama olmadan kaynak kodu olarak C# görünür.

 ![Kaynak olarak Meta Veriler](../csharp-ide/media/metadatasource.png "Meta veri kaynağı")

## <a name="viewing-metadata-as-source-in-the-code-definition-window"></a>Meta verileri kod tanımı penceresinde kaynak olarak görüntüleme
 **Kod tanımı** penceresi etkin veya görünür olduğunda, IDE, kod düzenleyicisinde imlecin altındaki öğeler ve **sınıf görünümü** veya **nesne tarayıcısı**seçili öğeler için otomatik olarak **Tanıma Git** komutunu yürütür. Kaynak kodu bu öğe için kullanılabilir durumda değilse IDE, **kod tanımı** penceresinde öğenin meta verilerini kaynak olarak görüntüler.

 Örneğin, imlecinizi kod düzenleyicisinde <xref:System.Console> sözcüğün içine yerleştirirseniz, <xref:System.Console> meta verileri **kod tanımı** penceresinde kaynak olarak görünür. Kaynak <xref:System.Console> bildirimine benzer, ancak bir uygulama olmadan.

 **Kod tanımı** penceresinde görüntülenen bir öğenin bildirimini görmek isterseniz, öğeye sağ tıklayın ve **Tanıma Git ' e**tıklayın.