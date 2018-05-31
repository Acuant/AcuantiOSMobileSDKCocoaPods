### 5.7

- Added support for rotating UI elements while the device is rotated 180 degrees in landscape mode. 

### 5.6

-  Added glare metrics for captured images. The metrics values can be accessed as follows: 

		BOOL hasGlare = [[_imageMetrics objectForKey:@"HAS_GLARE"] boolValue] 
		float glareGrade = [[_imageMetrics objectForKey:@"GLARE_GRADE"] floatValue]; 


In general, a GLARE_GRADE of 1 means no glare and 0 means there is a high chance of having a glare in the captured image.A glare grade 0.92f and above means there is no glare.

### 5.5

The **ImageMetrics** parameter was added to the following methods:

- **didCaptureCropImage**
- **barcodeScanTimeOut**
- **didCancelToCaptureData**
- **showiPadBrackets**


The **ImageMetrics** parameter specifies the sharpness and glare threshold of a cropped image. An image with a sharpness grade of 0.4f or above is considered a sharp image. In general, a GLARE_GRADE of 1 means no glare and 0 means there is a high chance of having a glare in the captured image. Users may set the threshold based on their requirements.


		BOOL isSharp = [[imageMetrics objectForKey:@"IS_SHARP"] boolValue]; 
		float sharpnessGrade = [[imageMetrics objectForKey:@"SHARPNESS_GRADE"] floatValue]; 

		BOOL hasGlare = [[_imageMetrics objectForKey:@"HAS_GLARE"] boolValue] 
		float glareGrade = [[_imageMetrics objectForKey:@"GLARE_GRADE"] floatValue]; 

  
### 5.4

-  Added new card type constant **AcuantCardTypeAuto**. If **AcuantCardTypeAuto** is set, then in **didCaptureCropImage** the last parameter will contain the automatically detected card type.

- Added the location parameter **cancelVisible** for the cancel button in the facial API

		+(id)presentFacialCaptureInterfaceWithDelegate
		(id<AcuantFacialCaptureDelegate>)delegate withSDK:
		(AcuantMobileSDKController*)sdkController inViewController:
		(UIViewController*)parentVC withCancelButton:(BOOL)cancelVisible
		withCancelButtonRect:(CGRect) cancelRect
		withWaterMark:(NSString* )watermarkText
		withBlinkMessage:(NSAttributedString*)message
		inRect:(CGRect)rect;

### 5.3

-  Added the **-(BOOL)isSDKValidated** API to check whether the SDK controller was validated.
-  Added Swift Sample Application
-  Added Swift AssureID Connect Sample Application
-  Added Objective-C AssureID Connect Sample Application
-  Added Objective-C Sample Application with AssureID Connect Data capture and AcuFill FRM

### 5.2

-  Removed the sourceImage property from AcuantCardProcessRequestOptions.

-  Added logtransaction property to AcuantCardProcessRequestOptions.If logging is enabled on the license key and logtransaction is set to true then transaction response is saved on the Acuant cloud for future retrieval.

-  Added the property imageSettings to AcuantCardProcessRequestOptions.The default value for imageSettings is -1. Please set this value to -1 always unless any special instruction is provided.

-  Removed "IsFacialEnabled" from the AcuantFacialData.

-  Added API to capture original image. By default it is disabled. [_instance setCanCaptureOriginalImage:YES];

-  Improved passport cropping

-  Added a delegate callback to capture the beginning of image capture event:

        (-(void)didTakeCardPhoto{
               NSLog(@"didTakeCardPhoto");
               //Add custom code
        }
-  Included Swift Sample application

### 5.1

-  Improved document cropping for IDs and Passports
-  Memory optimization
-  Fixed **FacialMatchConfidenceRating** data type issue. Data type is now integer.
-  Fixed **didCaptureOriginalImage** returns cropped images instead of original image
-  Modified the cropping delegate method
-  Added the **cardType** parameter:

        (void)didCaptureCropImage:(UIImage *)cardImage scanBackSide:(BOOL)scanBackSide andCardType:(AcuantCardType)cardType
