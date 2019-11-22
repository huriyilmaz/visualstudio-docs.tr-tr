---
title: Eski etkinlik tasarımcısını kullanma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- activities, configuring
- custom activities
- Activity Designer
- child activities, adding
- activities, adding child
- activities, creating custom
ms.assetid: 2fea8a05-6e58-423d-94bf-a822b15ffb80
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a13aeeb3394ee6b8896376c0e7d520b90fb56fa6
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302827"
---
# <a name="using-the-legacy-activity-designer"></a>Eski Etkinlik Tasarımcısını Kullanma
Bu konuda, eski [!INCLUDE[wfd1](../includes/wfd1-md.md)]etkinlik tasarımcısının nasıl kullanılacağı açıklanmaktadır. [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] veya [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]hedeflerken eski tasarımcıyı kullanın.

 Etkinlik Tasarımcısı kendi özel etkinliklerinizi oluşturmanıza olanak sağlar.

## <a name="creating-a-custom-activity"></a>Özel etkinlik oluşturma
 Etkinlik tasarımcısını kullanarak özel bir etkinlik oluşturmak için aşağıdaki adımları izleyin:

1. **Proje** menüsünde **etkinlik Ekle**' ye tıklayın.

2. **Etkinlik** veya **etkinlik (kod ayrımı ile)** şablonunu seçin.

   1. Etkinlik tanımı ve Kullanıcı kodu aynı kod dosyasında olan bir etkinlik oluşturmak için **etkinlik** şablonunu kullanın.

   2. Etkinlik tanımıyla iş akışı işaretlemesi ve Kullanıcı kodu ayrı bir kod dosyasında ifade edilen bir etkinlik oluşturmak için **etkinlik (kod ayrımı ile)** şablonunu kullanın.

3. Bir etkinlik adı yazın veya varsayılan adı koruyun ve ardından **Ekle**' ye tıklayın.

   Ayrıca, **Iş akışı etkinlik kitaplığı**türünde yeni bir proje oluşturarak özel etkinlik kümesi de oluşturabilirsiniz. Bu proje türü hakkında daha fazla bilgi için bkz. [nasıl yapılır: Iş akışı etkinlik kitaplığı oluşturma (eski)](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md).

## <a name="configuring-an-activity"></a>Etkinlik yapılandırma
 Etkinlik Tasarımcısı etkin olsa da, aşağıdaki tabloda listelenen özellikleri yapılandırmak için özellik tarayıcısını kullanabilirsiniz.

|Özellik|Açıklamalar|
|--------------|--------------|
|**Ad**|Etkinliğin adı.|
|**Temel sınıf**|Etkinliğin türetildiği temel sınıf. Varsayılan temel sınıf [SequenceActivity](https://go.microsoft.com/fwlink?LinkID=65020)'dir. **Özellikler** penceresinde, farklı bir temel sınıf **üç nokta** ( **...]** simgesini tıklayarak bir [.NET türü seçin iletişim kutusunda (eski)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md)bir temel sınıf seçin.|
|**Açıklama**|Etkinliğin Kullanıcı tanımlı açıklaması.|
|**Etkinletir**|Etkinlik yürütmeyi ve doğrulamayı etkinleştirmek için varsayılan olarak **true** olarak ayarlayın. Etkinlik yürütmeyi ve doğrulamayı devre dışı bırakmak için **false** olarak ayarlayın. Etkinlik yürütme ve doğrulama hakkında daha fazla bilgi için bkz. [Iş akışı etkinliklerini geliştirme](https://go.microsoft.com/fwlink?LinkID=65024).|

## <a name="adding-child-activities"></a>Alt etkinlikler ekleme
 Araç kutusundan alt etkinlikleri tasarlamakta olduğunuz etkinliğe sürükleyebilirsiniz. Ardından, her bir alt etkinliği Özellik tarayıcısını kullanarak yapılandırabilirsiniz.

## <a name="see-also"></a>Ayrıca Bkz.
 [Özel etkinlikler oluşturma](https://go.microsoft.com/fwlink?LinkID=65021) [Iş akışı etkinliklerini geliştirme](https://go.microsoft.com/fwlink?LinkID=65024) [eski Iş akışı etkinlikleri](../workflow-designer/legacy-workflow-activities.md) [özel etkinlikler örnek](https://go.microsoft.com/fwlink?LinkID=65022) nasıl yapılır: [eski iş akışı Tasarımcısı kullanarak](../workflow-designer/using-the-legacy-workflow-designer.md) [iş akışı etkinlik kitaplığı (eski) oluşturma](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md)