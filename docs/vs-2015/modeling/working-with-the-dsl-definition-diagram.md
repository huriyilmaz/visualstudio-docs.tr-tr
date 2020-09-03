---
title: DSL tanımı diyagramı ile çalışma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.diagram
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language Tools, diagram
- Domain-Specific Language Tools, Split Tree
- Domain-Specific Language Tools, Show Map Lines
- Domain-Specific Language Tools, Show As Class
- Domain-Specific Language Tools, Bring Tree Here
ms.assetid: 1a4c7a58-e134-438e-848e-efd98f92bf10
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 14e365d6bbe99634135bfad133d840b98e22e3b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663032"
---
# <a name="working-with-the-dsl-definition-diagram"></a>DSL Tanım Diyagramı ile Çalışma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir tanımın diyagramı, [!INCLUDE[dsl](../includes/dsl-md.md)] etki alanına özgü dili tanımlamaya yönelik önemli bir araçtır. Etki alanı modelinize öğeler ekleyebilir ve diyagramda ilişkiler tanımlayabilir ve diyagramın yerleşimini daha okunabilir hale getirmek için değiştirebilirsiniz.

## <a name="the-layout-of-the-diagram"></a>Diyagramın düzeni
 [!INCLUDE[dsl](../includes/dsl-md.md)]Tanım diyagramında iki bölüm, **sınıflar ve ilişkiler** bölümü ve **diyagram öğeleri** bölümü vardır. **Sınıflar ve ilişkiler** bölümü, etki alanı sınıflarını, etki alanı ilişkilerini ve devralmayı görüntüler. **Diyagram öğeleri** bölümünde şekil sınıfları, bağlayıcı sınıfları, kulvar sınıfları ve oluşturulan tasarımcı diyagramı görüntülenir.

 Etki alanı sınıfları **sınıflar ve ilişkiler** bölümlerinde birden çok konumda görünebilir. Bir etki alanı sınıfı tanımı, diğer etki alanı sınıflarının temel sınıfı ise devralma ağacını ve ekleme veya başvuru ilişkilerinin kaynağı ise bir ilişki ağacını görüntüler. Etki alanı sınıfı yer tutucuları ekleme veya başvuru ilişkilerinin hedefleri olarak görünür. Varsayılan olarak, yer tutucu öğeleri, **etki alanı özellikleri** bölmesi daraltılmış olarak görüntülenir. Devralma veya başvuru ilişkilerini göstermez.

 Bir etki alanı sınıfı eklediğinizde, **sınıflar ve ilişkiler** bölümünün alt kısmında görünür. Bir katıştırma veya başvuru ilişkisi eklediğinizde, kaynak etki alanı sınıfının sağına ve sağına çizilir.

 Etki alanı sınıfları ve ilişkileri eklerken, belirli bir etki alanı sınıfının bulunması zor olabilir. Bir etki alanı sınıfını **DSL Gezgininde** sağ tıklayıp **diyagramda Konumlandır**' a tıklayarak bulabilirsiniz.

 Aşağıdaki bölümlerde, daha kolay okunmasını sağlamak için diyagramın görünümünü nasıl değiştirebileceğiniz açıklanır.

## <a name="copying-elements"></a>Öğeleri kopyalama
 DSL tanımı diyagramında öğeleri kopyala, kes ve yapıştır işlemlerini kullanabilirsiniz.

## <a name="zooming-in-or-out-on-the-diagram"></a>Diyagramda yakınlaştırma veya uzaklaştırma
 Yakınlaştırma düzeyini ayarlamak için **DSL Tasarımcısı** araç çubuğunu kullanarak diyagramda yakınlaştırma veya uzaklaştırma yapabilirsiniz.

## <a name="hiding-map-lines"></a>Harita çizgilerini gizleme
 Harita çizgileri, bir etki alanı sınıfı ya da etki alanı ilişkisi ile eşlendiği şekil veya bağlayıcı arasına çizilen satırlar olur. Harita çizgilerini, **DSL Tasarımcısı** araç çubuğunda **harita çizgilerini göster** düğmesine tıklayarak gizleyebilirsiniz. Satırları göstermek için düğmeye tekrar tıklayın.

## <a name="changing-the-diagram-layout"></a>Diyagram yerleşimini değiştirme
 **Sınıfların ve ilişki** bölümünün yerleşimini aşağıdaki şekilde değiştirebilirsiniz.

### <a name="expandcollapse"></a>Genişlet/Daralt
 Bir etki alanı sınıfını veya bir şekli temsil eden bir bölme şekli öğesinin boyutunu, sağ tıklayıp **Daralt**' a tıklayarak azaltabilirsiniz. Bu, şeklin **etki alanı özellikleri** bölmesini gizler. **Etki alanı özellikleri** bölmesini yeniden göstermek için şekle sağ tıklayın ve ardından **Genişlet**' e tıklayın.

### <a name="move-updown"></a>Yukarı/aşağı taşı
 Bir etki alanı sınıfını veya diyagramı öğesini bölüme sağ tıklayıp aşağı **Taşı** veya **aşağı taşı**' ya tıklayarak bölüm içinde yukarı veya aşağı taşıyabilirsiniz. Bir katıştırma veya başvuru ilişkisinin hedefi olarak görüntülenen bir yer tutucu öğesini taşırsanız, ilişki onunla birlikte hareket eder.

### <a name="expandcollapse-relationships-tree"></a>Ilişki ağacını Genişlet/Daralt
 Bir etki alanı sınıfı, diğer etki alanı sınıflarıyla katıştırma veya başvuru ilişkilerinde kaynak rolü oynadığında, etki alanı sınıf tanımına sağ tıklayıp **Ilişkiler ağacını Daralt**' a tıklayarak ilişkileri gizleyebilirsiniz. İlişkileri göstermek için, tanım öğesine sağ tıklayın ve ardından **Ilişkiler ağacını Genişlet**' e tıklayın.

### <a name="expandcollapse-inheritance-tree"></a>Devralma ağacını Genişlet/Daralt
 Bir etki alanı sınıfı, diğer etki alanı sınıflarının temel sınıfı ise, etki alanı sınıf tanımına sağ tıklayıp **Devralma ağacını Daralt**' a tıklayarak devralma ağacını gizleyebilirsiniz. Devralma ağacını göstermek için, tanım öğesine sağ tıklayın ve ardından **Devralma ağacını Genişlet**' e tıklayın.

### <a name="bring-tree-here"></a>Buraya Ağacı Getir
 Bir yer tutucu etki alanı sınıfına sağ tıklayıp daha sonra **ağacı getir**' e tıklayarak diyagramı birleştirebilirsiniz. Yer tutucu etki alanı sınıfı bir tanım öğesi haline gelir ve devralma ve ilişki ağaçlarını görüntüler. Önceki tanım öğesi bir ilişkinin hedefi veya bir devralma ilişkisindeki alt öğe ise yer tutucu bir öğe olur; Aksi takdirde, kaybolur.

### <a name="split-tree"></a>Ağacı Böl
 Devralma veya ilişki ağaçlarını, onları görüntüleyen etki alanı sınıfı tanımına sağ tıklayıp ardından **bölünmüş ağaç**' a tıklayarak kesebilirsiniz. Tanım öğesi bir yer tutucu öğesi haline gelir ve tanım etki alanı sınıfı, devralma ve ilişki ağaçları ile birlikte artık bölümün en altında görüntülenir.

### <a name="show-as-class"></a>Sınıf Olarak Göster
 Bir etki alanı ilişkisinde türetilmiş ilişkiler varsa veya diğer etki alanı ilişkileri ile katıştırma veya başvuru ilişkisi varsa, ilişkiye sağ tıklayıp **sınıf olarak göster**' e tıklayarak ilişkiyi bir sınıf olarak görüntüleyebilirsiniz. İlişki, bir **etki alanı özellikleri** bölmesi ile birlikte görüntülenir ve devralma ve ilişki ağaçlarını gösterir.

## <a name="see-also"></a>Ayrıca Bkz.
 [Alana Özgü Dil Araçları sözlüğü](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
