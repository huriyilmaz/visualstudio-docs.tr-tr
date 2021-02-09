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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 65f225f8e3dd3f6d2b3afb2d2a5284d172d4fab1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891299"
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