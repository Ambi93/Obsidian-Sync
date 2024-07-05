/* @settings

name: Modular CSS Layout - Multi Column
id: modular-css-layout-mc
settings:

    -
        id: multi-column-title
        title: Multi Column Callout Settings
        type: heading
        level: 1
		collapsed: true

	-
        id: mc-callout-general-title
        title: MCC -- General
        type: heading
        level: 2
		collapsed: false
	-
		id: mcc-img-snw-display
		title: Hide SNW indicator for images in MC Callout
		type: variable-select
		default: none
		options:
			-
				label: Show
				value: inline
			-
				label: Hide
				value: none

	-
        id: mc-callout-width-title
        title: MCC -- Width
        type: heading
        level: 2
		collapsed: false
    -
        id: callout-min-width
        title: Minimum Sub-Callout Width
        description: for sub-callout in [!multi-column]. in px units
        type: variable-number-slider
        default: 200
        min: 100
        max: 500
        step: 50
		format: px
	-
        id: callout-nowrap-min-width
        title: Minimum NO-WRAP Sub-Callout Width
        description: for sub-callout in [!multi-column|no-wrap]. in px units
        type: variable-number-slider
        default: 250
        min: 100
        max: 500
        step: 50
		format: px

	-
        id: mc-callout-gap-title
        title: MCC -- Gap & Margin
        type: heading
        level: 2
		collapsed: false
    -
        id: callout-gap
        title: Sub-Callout Gap (any unit)
        description: NO spacing between figure and unit
        type: variable-text
        default: 1em
	-
		id: callout-margin
		title: Sub-Callout Margin (any unit)
		description: to allow some spacing for box-shadow
		type: variable-text
		default: 0px



	-
        id: float-callout-title
        title: Float Callout Settings
        type: heading
        level: 1
		collapsed: true

	-
        id: float-callout-general-title
        title: FC -- General
        type: heading
        level: 2
		collapsed: false

	-
		id: float-callout-snw-display
		title: Hide SNW indicator in Callout Float / Aside
		type: variable-select
		default: none
		options:
			-
				label: Show
				value: inline-block
			-
				label: Hide
				value: none

	-
        id: float-width-title
        title: FC -- Width
        type: heading
        level: 2
		collapsed: false
    -
        id: float-small-width
        title: Floating Callout Width - Small (in px)
        type: variable-number-slider
        default: 300
        min: 200
        max: 450
        step: 50
		format: px
    -
        id: float-medium-width
        title: Floating Callout Width - Medium (in px)
        type: variable-number-slider
        default: 400
        min: 300
        max: 550
        step: 50
		format: px
    -
        id: float-large-width
        title: Floating Callout Width - Large (in px)
        type: variable-number-slider
        default: 600
        min: 500
        max: 750
        step: 50
		format: px

	-
        id: float-gap-title
        title: FC -- Gap & Margin
        type: heading
        level: 2
		collapsed: false
	-
	    id: float-callout-top-margin
		title: Adjust top margin for Float Left and Float Right
		description: Can use em or px unit
	    type: variable-text
	    default: 0em
	-
	    id: float-left-callout-margin-inline
		title: Adjust left-right margin for Float Left Callout
		description: Enter in this order - "left right". Can use em or px unit
		type: variable-text
	    default: 0px 12px
	-
	    id: float-right-callout-margin-inline
		title: Adjust left-right margin for Float Right Callout
		description: Enter in this order - "left right". Can use em or px unit
	    type: variable-text
	    default: 12px 0px



    -
        id: mc-list-column-title
        title: List Column
		description: using `{.xxx-column-list-xxx}` and `#mcl/list-column`
        type: heading
        level: 1
		collapsed: true
	-
        id: list-column-width-title
        title: Width control for List Column
        type: heading
        level: 2
		collapsed: false
    -
        id: list-min-width
        title: Minimum Column Width (in px)
        type: variable-number-slider
        default: 200
        min: 100
        max: 500
        step: 50
		format: px

	-
        id: list-column-deco-title
        title: Decoratives control for List Column
        type: heading
        level: 2
		collapsed: false
	-
        id: col-rule-width
        title: Ruler (vertical line between columns) width for List Column
		description: in px unit. Set to 0 to disable ruler
        type: variable-number-slider
        default: 1
        min: 0
        max: 4
        step: 1
		format: px
    -
        id: col-rule-color
        title: Ruler (vertical line between columns) color for List Column
		type: variable-themed-color
		format: hsl
		opacity: true
		default-light: '#'
		default-dark: '#'


	-
        id: mc-list-grid-title
        title: List Grid and List Card
		description: using `#mcl/list-grid` and `#mcl/list-card`
        type: heading
        level: 1
		collapsed: true

	-
        id: list-grid-card-width-title
        title: Width control for List Grid and List Card
        type: heading
        level: 2
		collapsed: false
	-
        id: list-grid-min-width
        title: Minimum width for normal List Grid/Card
		description: For `#mcl-list-grid` or `#mcl-list-card`. Can use em or px unit
		type: variable-text
		default: 250px
	-
        id: list-grid-wide-min-width
        title: Minimum width for Wide List Grid/Card
		description: For `#mcl/list-grid-wide` or `#mcl/list-card-wide`. Can use em or px unit
		type: variable-text
		default: 350px

	-
        id: list-card-deco-title
        title: Decoratives control for List Card
        type: heading
        level: 2
		collapsed: false
	-
		id: mcl-card-header-border-width
		title: Bottom border for first header in List Card
		description: Can use em or px unit. Set to 0 to disable the border
		type: variable-text
		default: 1px
	-
		id: mcl-card-bg-color
		title: Background color for List Card
		type: variable-themed-color
		format: hsl
		opacity: true
		default-light: '#'
		default-dark: '#'
	-
        id: mcl-card-gap
        title: Gap between cards for List Card
		description: Can use em or px unit
		type: variable-text
		default: 0.2em
	-
        id: mcl-card-border-width
        title: Border width for each card in List Card
		description: Can use em or px unit. Set to 0 to disable the border
		type: variable-text
		default: 1px
	-
		id: mcl-card-border-color
		title: Border color for each card in List Card
		type: variable-themed-color
		format: hsl
		opacity: true
		default-light: '#'
		default-dark: '#'

*/