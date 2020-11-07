---
title: '&lt;publisherIdentity &gt; öğesi (ClickOnce dağıtımı) | Microsoft Docs'
description: PublisherIdentity öğesi, bir dağıtım bildirimini imzalayan yayımcı hakkında bilgiler içerir. İmzalı bildirimler için öğesi gereklidir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publisherIdentity Element [ClickOnce deployment manifest], introduction
- required element for signed manifests [ClickOnce], publisherIdentity Element
- publisherIdentity Element [ClickOnce deployment manifest], syntax, elements, and attributes
ms.assetid: 34c579db-d2f2-4b66-b9c8-47207f33d950
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1eb4b67bfdca13c63480f3dde82004d87cd4a12a
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94350692"
---
# <a name="ltpublisheridentitygt-element-clickonce-deployment"></a>&lt;publisherIdentity &gt; öğesi (ClickOnce dağıtımı)
Bu dağıtım bildirimini imzalayan yayımcı hakkındaki bilgileri içerir.

## <a name="syntax"></a>Syntax

```xml
<publisherIdentity
   name
   issuerKeyHash
/>
```

## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler
 `publisherIdentity`İmzalı bildirimler için öğesi gereklidir. Aşağıdaki tabloda, `publisherIdentity` öğesinin desteklediği öznitelikler gösterilmektedir.

|Öznitelik|Açıklama|
|---------------|-----------------|
|`name`|Gereklidir. Bu uygulamayı yayımlayan tarafın kimliğini açıklar.|
|`issuerKeyHash`|Gereklidir. Sertifika verenin ortak anahtarının SHA-1 karmasını içerir.|

#### <a name="parameters"></a>Parametreler

## <a name="property-valuereturn-value"></a>Özellik değeri/dönüş değeri

## <a name="exceptions"></a>Özel durumlar

## <a name="remarks"></a>Açıklamalar

## <a name="requirements"></a>Gereksinimler

## <a name="subhead"></a>Alt başlık