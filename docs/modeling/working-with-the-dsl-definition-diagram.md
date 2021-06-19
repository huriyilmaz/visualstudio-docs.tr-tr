---
title: DSL Tanım Diyagramı ile Çalışma
description: DSL Araçları tanımının diyagramının etki alanına özgü bir dil tanımlamaya yönelik önemli bir araç olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f401fe0509fc425fff873a7dc224c69359156861
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388080"
---
# <a name="working-with-the-dsl-definition-diagram"></a>DSL Tanım Diyagramı ile Çalışma
Tanım diyagramı, [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] etki alanına özgü dili tanımlamaya yönelik önemli bir araçtır. Etki alanı modelinize öğe ekleyebilir ve diyagramda ilişkiler tanımlayabilir ve diyagramın düzenini değiştirerek daha okunabilir hale ebilirsiniz.

## <a name="the-layout-of-the-diagram"></a>Diyagramın Düzeni
 Tanım [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] diyagramı iki bölüme sahiptir: **Sınıflar ve İlişkiler** bölümü ve **Diyagram Öğeleri** bölümü. Sınıflar **ve İlişkiler bölümü etki** alanı sınıflarını, etki alanı ilişkilerini ve devralmayı görüntüler. Diyagram **Öğeleri bölümü** şekil sınıflarını, bağlayıcı sınıflarını, kulan sınıflarını ve oluşturulan tasarımcı diyagramını görüntüler.

 Etki alanı sınıfları, Sınıflar ve İlişkiler bölümleri **içinde birden çok konumda** görünebilir. Bir etki alanı sınıf tanımı, diğer etki alanı sınıfları için temel sınıfsa bir devralma ağacı ve ekleme veya başvuru ilişkilerinin kaynağı ise bir ilişkiler ağacı görüntüler. Etki alanı sınıfı yer tutucuları ekleme veya başvuru ilişkilerinin hedefleri olarak görünür. Varsayılan olarak, yer tutucu öğeleri Etki Alanı **Özellikleri bölmesi daraltılmış** olarak görüntülenir. Devralma, ekleme veya başvuru ilişkilerini göstermezler.

 Bir etki alanı sınıfı eklerken, sınıf Sınıflar ve İlişkiler bölümünün **alt kısmında** görünür. Ekleme veya başvuru ilişkisi eklerken, bu ilişki kaynak etki alanı sınıfının altında ve sağ tarafından çizilir.

 Etki alanı sınıfları ve ilişkileri eklerken belirli bir etki alanı sınıfını bulmak zor olabilir. DSL Gezgini'nde sağ tıklar ve  ardından Diyagramda Bul'a tıklayarak bir etki **alanı sınıfı bulabilirsiniz.**

 Aşağıdaki bölümlerde, daha kolay okunacak şekilde diyagramın görünümünü nasıl değiştirebilirsiniz?

## <a name="copying-elements"></a>Öğeleri kopyalama
 DSL tanım diyagramında öğelerde kopyalama, kesme ve yapıştırma kullanabilirsiniz.

## <a name="zooming-in-or-out-on-the-diagram"></a>Diyagramda Yakınlaştırma veya Uzaklaştırma
 Yakınlaştırma düzeyini ayarlamak için araç çubuğunu kullanarak diyagramı **yakınlaştırabilir DSL Tasarımcısı** yakınlaştırabilirsiniz.

## <a name="hiding-map-lines"></a>Harita Çizgilerini Gizleme
 Eşleme çizgileri, bir etki alanı sınıfı veya etki alanı ilişkisi ile eşlenmiş olduğu şekil veya bağlayıcı arasında çizilen satırlardır. Harita çizgilerini gizlemek için araç **çubuğundaki Harita** Çizgilerini Göster **düğmesine DSL Tasarımcısı** ekleyebilirsiniz. Satırları göstermek için düğmeye yeniden tıklayın.

## <a name="changing-the-diagram-layout"></a>Diyagram Düzenini Değiştirme
 Sınıflar ve İlişkiler bölümünün **düzenini aşağıdaki gibi** değiştirebilirsiniz.

### <a name="expandcollapse"></a>Genişlet/Daralt
 Bir etki alanı sınıfını veya bir şekli temsil eden bölme şekil öğesinin boyutunu, sağ tıklar ve ardından Daralt'a **tıklayarak azaltabilirsiniz.** Bu, **şeklin Etki Alanı Özellikleri** bölmelerini gizler. Etki Alanı Özellikleri **bölmesini yeniden** göstermek için şekle sağ tıklayın ve genişlet'e **tıklayın.**

### <a name="move-updown"></a>Yukarı/Aşağı Taşı
 Bir etki alanı sınıfını veya diyagram öğesini öğeye sağ tıklar ve sonra Yukarı Taşı veya Aşağı Taşı'ya tıklayarak bölümde **yukarı** veya aşağı **taşıabilirsiniz.** Ekleme veya başvuru ilişkisinin hedefi olarak görüntülenen bir yer tutucu öğesini taşımanız, ilişki ile birlikte hareket eder.

### <a name="expandcollapse-relationships-tree"></a>İlişkiler Ağacını Genişletme/Daraltma
 Bir etki alanı sınıfı, diğer etki alanı sınıflarında ekleme veya başvuru ilişkilerinde kaynak rolü oynarsa, etki alanı sınıf tanımına sağ tıklar ve ardından İlişkiler Ağacını Daralt'a tıklayarak **ilişkileri gizleyebilirsiniz.** İlişkileri göstermek için tanım öğesine sağ tıklayın ve ardından İlişkiler Ağacını **Genişlet'e tıklayın.**

### <a name="expandcollapse-inheritance-tree"></a>Devralma Ağacını Genişletme/Daraltma
 Bir etki alanı sınıfı diğer etki alanı sınıflarının temel sınıfı ise, etki alanı sınıf tanımına sağ tıklar ve Devralma Ağacını Daralt'a tıklayarak devralma **ağacını gizleyebilirsiniz.** Devralma ağacını göstermek için tanım öğesine sağ tıklayın ve ardından Devralma Ağacını **Genişlet'e tıklayın.**

### <a name="bring-tree-here"></a>Buraya Ağacı Getir
 Bir yer tutucu etki alanı sınıfına sağ tıklar ve ardından Ağacı Buraya **Getir'e tıklayarak diyagramı birleştirebilirsiniz.** Yer tutucu etki alanı sınıfı bir tanım öğesi haline gelir ve devralma ile ilişkiler ağaçlarını görüntüler. Bir ilişkinin hedefi veya devralma ilişkisinde alt öğe ise, eski tanım öğesi bir yer tutucu öğe olur; aksi takdirde kaybolur.

### <a name="split-tree"></a>Ağacı Böl
 Bunları görüntüleyen etki alanı sınıf tanımına sağ tıklar ve ardından Ağacı Böl'e tıklayarak devralma veya ilişkiler **ağaçlarını ayırabilirsiniz.** Tanım öğesi bir yer tutucu öğesi haline gelir ve tanım etki alanı sınıfı, devralma ve ilişki ağaçlarıyla birlikte bölümün en altında görüntülenir.

### <a name="show-as-class"></a>Sınıf Olarak Göster
 Bir etki alanı ilişkisi türetilmiş ilişkilere sahipse veya başka etki alanı ilişkileriyle ekleme veya başvuru ilişkilerine sahipse, ilişkiye sağ tıklar ve ardından Sınıf Olarak Göster'e tıklayarak ilişkiyi bir sınıf **olarak görüntüebilirsiniz.** İlişki bir Etki Alanı Özellikleri **bölmesiyle görüntülenir** ve devralma ile ilişkiler ağaçlarını gösterir.

## <a name="see-also"></a>Ayrıca bkz.

- [Alana Özgü Dil Araçları Sözlüğü](/previous-versions/bb126564(v=vs.100))