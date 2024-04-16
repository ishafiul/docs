# Barikoi Consumer Mobile App - Map Screen

## Reverse Geo Bottom Sheet

This bottom sheet will appear when a location point is tapped. It contains details about that geo
point:

Images

- Address name
- Latitude and longitude
- Directions
- Call information
- Suggest an edit
  File location: lib/presentation/ui/bottom_sheet/reverse_geo_info.dart

Here, the `ReverseGeoInfo` widget will take place info (`ReverseGeoPlace`) and render all widgets
accordingly.

### Image Grid View

`ImageGrid` is a custom widget responsible for displaying a grid layout for image view. The number
of images can be dynamic here, and it will adjust the grid based on the image count. This widget
also contains `ImageUploader`.

### Image Uploader

`ImageUploader` is a custom widget to make the image upload process easy for geo points.

This widget can take multiple images, and upon sending, it will request multiple file uploads
simultaneously. This widget also comes with the `ImageGrid` widget. If the user is logged in, they
will be able to upload images for a geo point.

`ImageUploader` will take a parameter placeCode, which is a string. Based on this place code, upon
sending, `UploadImageBloc`'s `UploadImageEvent.sendImages` will be called.

## BottomSheetChip

this is a reusable chip widget that will show during place info view. in this project its used as a
horizontal scrollable list.
Main chip content are

- direction
- call
- share location
- suggest an edit

`BottomSheetChip` contain 2 style of chip (`BottomSheetChipType`).

- fill (`BottomSheetChipType.fill`),
- outline (`BottomSheetChipType.outline`)

### Parameters

| Param                     | Description                                                                                                            |
|---------------------------|------------------------------------------------------------------------------------------------------------------------|
| SvgPicture svgIcon        | `svgIcon` will take a `SvgPicture` as will use as a prefix for this chip widget                                        |
| BottomSheetChipType? type | type will define style of the chip. there are 2 type only `BottomSheetChipType.fill` and `BottomSheetChipType.outline` |
| Function()? onTap         | a callback function for the chip wich will trigger on tap.                                                             |
| String title              | diplay text or title for the chip.                                                                                     |

## PlaceInfoBottomSheet

This widget combines the display of place information, whether it's from autocomplete or from
reverse geocode API.

### Parameters

| Param                                    | Description                                                                            |
|------------------------------------------|----------------------------------------------------------------------------------------|
| ReverseGeoPlace? reverseGeoPlace         | place data form reverse geo code api. in the project main model is `ReverseGeoPlace`   |
| AutoCompleteResponse? autocompletePlace; | place data form auto complete api. in the project main model is `AutoCompleteResponse` |

note: this widget contain 2 kind of assert error. `Either reverseGeoPlace or autocompletePlace must be provided, and not both at the same time.`