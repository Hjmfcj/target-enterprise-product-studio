# MTN Sudan — Travel Mission Management System
## Production-Ready Figma Structure & Design Specification

---

# PHASE 1 — ISSUES FOUND IN EXISTING HTML DESIGN

The following elements in `MTN_Travel_System_UX_Design.html` are **not supported** by the requirements document and must be removed before any design work:

| # | Issue Location in HTML | Violation | Action |
|---|---|---|---|
| 1 | IA Node: "Archived (Rejected)" screen listed in nav tree | "Archived" is not a defined status in the requirements | **REMOVE** |
| 2 | User flow step: "mission archived, employee notified" on rejection | No "Archived" status exists. Rejected missions are simply Rejected | **REPLACE** with status = Rejected only |
| 3 | Workflow step 6: "Finance GL records the amounts; HR logs employee absence" | Finance GL integration and HR absence management are explicitly excluded | **REMOVE** |
| 4 | Workflow step 8: "Employee notified — System notification" | Notification module is not defined in requirements | **REMOVE** |
| 5 | Travel Cost Review screen: "Submit to Finance GL →" button | Finance GL integration does not exist in requirements | **REMOVE** button; replace with "Submit to Treasury" |
| 6 | Approval card: LM/DM notification trigger described as automatic system notification | Not defined in requirements | **REMOVE** notification language |
| 7 | User flow: description states "Destination list is configurable by the Travel Team" | Requirements state destination list is configurable (no specific role assigned in requirements) | **NEUTRAL** — leave as system configuration, no role attached |
| 8 | No "My Missions" screen present | Requirements explicitly list "My Missions" under Mission Management nav group | **ADD** My Missions screen |
| 9 | Delta/trend indicators (↑↑) on KPI cards in Dashboard | Trend analytics not defined in requirements | **REMOVE** delta indicators |
| 10 | Workflow tracker shows Finance GL and HR as post-payment steps | Neither is a defined workflow step | **REMOVE** both steps from workflow tracker |

**Confirmed clean items in HTML (keep):**
- Color palette (MTN Yellow #FFCB00, Black #1A1A1A) ✓
- All 11 status pills and their semantic colors ✓
- Form field patterns ✓
- Workflow tracker component ✓
- Settlement balance card (positive/negative/zero) ✓

---

# PHASE 2 — FIGMA STRUCTURE

---

## 2.1 FIGMA PAGES

```
Page 1 ── 🎨 Design Tokens
Page 2 ── 🧩 Component Library
Page 3 ── 📐 Wireframes (Lo-Fi)
Page 4 ── 🖥 Screens — Mission Management
Page 5 ── 🖥 Screens — Approvals & Review
Page 6 ── 🖥 Screens — Operations
Page 7 ── 🖥 Screens — Finance & Reports
Page 8 ── 🔄 Prototyping Flows
Page 9 ── 📋 Handoff Notes
```

---

## 2.2 DESIGN TOKENS

### 2.2.1 Color Tokens

```
── Brand ──────────────────────────────────────────────
color/brand/primary          #FFCB00    MTN Yellow
color/brand/primary-dark     #E6B800    Yellow hover/pressed
color/brand/primary-light    #FFF8D6    Yellow tint (backgrounds)
color/brand/black            #1A1A1A    MTN Black
color/brand/dark             #0F0F0F    Sidebar background

── Neutral ────────────────────────────────────────────
color/neutral/white          #FFFFFF
color/neutral/50             #F9FAFB    Page background
color/neutral/100            #F4F5F7    Section background
color/neutral/200            #E5E7EB    Dividers / borders
color/neutral/300            #D1D5DB    Input borders
color/neutral/400            #9CA3AF    Placeholder / label muted
color/neutral/500            #6B7280    Body muted
color/neutral/700            #374151    Body default
color/neutral/900            #2B2B2B    Heading

── Semantic ───────────────────────────────────────────
color/semantic/success       #16A34A    Approved / Active
color/semantic/success-bg    #DCFCE7
color/semantic/warning       #D97706    Extended / pending
color/semantic/warning-bg    #FEF3C7
color/semantic/danger        #DC2626    Rejected
color/semantic/danger-bg     #FEE2E2
color/semantic/info          #2563EB    Links / mission IDs
color/semantic/info-bg       #DBEAFE
color/semantic/purple        #7C3AED    Pending statuses
color/semantic/purple-bg     #EDE9FE
color/semantic/sky           #0369A1    Travel Review status
color/semantic/sky-bg        #E0F2FE
color/semantic/emerald       #065F46    Completed
color/semantic/emerald-bg    #D1FAE5

── Surface ────────────────────────────────────────────
color/surface/card           #FFFFFF
color/surface/page           #F2F4F7
color/surface/sidebar        #0F0F0F
color/surface/table-head     #FAFAFA
color/surface/row-hover      #FAFAFA
color/surface/input          #FFFFFF
color/surface/input-focus-ring  rgba(255,203,0,0.15)
```

### 2.2.2 Typography Tokens

```
── Font Families ──────────────────────────────────────
font/family/display     'Space Grotesk', sans-serif   (headings, page titles)
font/family/body        'Inter', sans-serif            (all body text, labels, inputs)
font/family/mono        'JetBrains Mono', monospace   (IDs, codes, amounts)

── Font Sizes ─────────────────────────────────────────
font/size/2xs     10px    (badge text, uppercase labels)
font/size/xs      11px    (meta labels, column headers)
font/size/sm      12px    (table cells, small body)
font/size/base    13px    (default body)
font/size/md      14px    (card body, form hints)
font/size/lg      16px    (card titles)
font/size/xl      18px    (section subtitles)
font/size/2xl     22px    (balance amounts)
font/size/3xl     26px    (KPI values)
font/size/4xl     32px    (hero amounts)

── Font Weights ───────────────────────────────────────
font/weight/regular   400
font/weight/medium    500
font/weight/semibold  600
font/weight/bold      700
font/weight/extrabold 800

── Line Heights ───────────────────────────────────────
font/leading/tight    1.2
font/leading/snug     1.35
font/leading/normal   1.5
font/leading/relaxed  1.6

── Letter Spacing ─────────────────────────────────────
font/tracking/tight    -0.01em
font/tracking/normal    0
font/tracking/wide     0.05em
font/tracking/wider    0.1em
font/tracking/widest   0.15em
```

### 2.2.3 Spacing Tokens

```
space/0       0px
space/1       4px
space/2       8px
space/3       12px
space/4       16px
space/5       20px
space/6       24px
space/8       32px
space/10      40px
space/12      48px
space/16      64px
space/20      80px

── Named Aliases ──────────────────────────────────────
space/page-padding          24px   (hifi-page-body padding)
space/card-padding          20px   (card internal padding)
space/card-padding-sm       16px   (compact card)
space/form-gap              14px   (between form fields)
space/section-gap           20px   (between page sections)
space/topbar-height         64px
space/sidebar-width         240px
```

### 2.2.4 Border Radius Tokens

```
radius/none     0px
radius/sm       6px    (buttons, inputs, small badges)
radius/md       10px   (cards, panels, modals)
radius/lg       14px   (large cards)
radius/full     9999px (status pills, avatar badges)
```

### 2.2.5 Shadow Tokens

```
shadow/sm    0 1px 3px rgba(0,0,0,0.08), 0 1px 2px rgba(0,0,0,0.04)
shadow/md    0 4px 6px rgba(0,0,0,0.07), 0 2px 4px rgba(0,0,0,0.05)
shadow/lg    0 10px 15px rgba(0,0,0,0.08), 0 4px 6px rgba(0,0,0,0.05)
shadow/focus-yellow   0 0 0 3px rgba(255,203,0,0.25)
shadow/focus-blue     0 0 0 3px rgba(37,99,235,0.2)
```

### 2.2.6 Grid & Layout Tokens

```
grid/columns/page      12
grid/gutter            24px
grid/margin            32px
grid/breakpoint/sm     768px
grid/breakpoint/md     1024px
grid/breakpoint/lg     1280px
grid/breakpoint/xl     1440px
```

---

## 2.3 COMPONENT LIBRARY

### 2.3.1 Component Index

```
Atoms
  ├── Button
  ├── StatusPill
  ├── Badge / Counter
  ├── Avatar
  ├── Icon (tabler-icons)
  ├── Divider
  └── Spinner

Molecules
  ├── FormField (Label + Input + HelperText)
  ├── SelectField
  ├── DateField
  ├── TextareaField
  ├── FileUploadField
  ├── CalcPreviewRow
  ├── TableRow
  ├── NavItem
  ├── KPICard
  ├── WorkflowStep
  └── AlertBanner

Organisms
  ├── Sidebar
  ├── Topbar
  ├── DataTable
  ├── MissionCard (list view)
  ├── ApprovalCard
  ├── WorkflowTracker
  ├── SettlementBalanceCard
  ├── FilterBar
  └── EmptyState

Templates
  ├── PageShell (Sidebar + Topbar + Content area)
  ├── FormPageLayout
  ├── ListPageLayout
  └── DetailPageLayout
```

---

### 2.3.2 Component Variants

#### Button
```
Component name: Button
Frame: Auto Layout, Horizontal, Gap 6px, Padding H 18px V 8px
Radius: radius/sm (6px)

Variants:
  variant = Primary
    background: color/brand/primary (#FFCB00)
    color: color/brand/black
    font: 12px/700/Inter
    shadow: none
    hover: background color/brand/primary-dark
    
  variant = Secondary (Outline)
    background: transparent
    border: 1.5px color/neutral/300
    color: color/neutral/700
    hover: background color/neutral/100

  variant = Danger
    background: color/semantic/danger
    color: white
    hover: background #B91C1C

  variant = Ghost
    background: transparent
    color: color/neutral/500
    hover: background color/neutral/100

  variant = Success
    background: color/semantic/success
    color: white
    hover: background #15803D

States per variant: default / hover / focused / disabled / loading
Size modifier: sm (height 28px), md (height 36px, DEFAULT), lg (height 44px)
Icon slot: Left icon, Right icon, Icon-only
```

#### StatusPill
```
Component name: StatusPill
Frame: Auto Layout, Horizontal, Gap 5px, Padding H 10px V 3px
Radius: radius/full (9999px)
Font: 10.5px/500/Inter

Variants (status + color pair):
  Draft               bg #F3F4F6      text #6B7280
  Pending LM          bg #EDE9FE      text #7C3AED
  Pending DM          bg #FEF3C7      text #D97706
  Pending Travel      bg #E0F2FE      text #0369A1
  Pending Payment     bg #DCFCE7      text #15803D
  Mission Active      bg #DCFCE7      text #15803D
  Mission Extended    bg #FEF3C7      text #92400E
  Mission Closed      bg #F3F4F6      text #374151
  Pending Settlement  bg #EDE9FE      text #7C3AED
  Completed           bg #D1FAE5      text #065F46
  Rejected            bg #FEE2E2      text #DC2626

Dot indicator: 6px circle, same color as text, margin-right 4px
```

#### KPICard
```
Component name: KPICard
Frame: 1fr grid cell, padding 16px 20px, radius/md, shadow/sm
Border: 1px color/neutral/200

Slots:
  value        font 26px/700/Space Grotesk, color brand/black
  label        font 12px/400/Inter, color neutral/500
  icon         24px icon, top-right, color neutral/400

Variants:
  default     white background
  highlighted background color/brand/primary-light, border color/brand/primary

NO delta/trend indicators. Not in requirements.
```

#### WorkflowTracker
```
Component name: WorkflowTracker
Frame: Auto Layout Horizontal, overflow-x scroll, gap 0, padding 16px 20px
Background: white

Steps (always 9, fixed):
  1. Draft
  2. Line Manager
  3. Division Manager
  4. Travel Review
  5. Payment
  6. Active
  7. [Closed — only rendered if mission extended, shows "Extended" label]
  8. Mission Closure
  9. Settlement → Completed

Each WorkflowStep:
  Frame: Auto Layout Vertical, align center, min-width 90px
  Connector line: absolute positioned, top 16px, left 60%, width calc(100%-20px), height 2px

  States:
    done    icon bg color/brand/primary, icon color black, connector color/brand/primary
    active  icon bg white, icon border 2px brand/primary, box-shadow shadow/focus-yellow
    pending icon bg color/neutral/200, icon color neutral/400, connector neutral/200

  Label: 10px/500/Inter, neutral/400 (pending), neutral/700 (done/active)

IMPORTANT: No Finance GL step. No HR Absence step. Steps end at "Completed".
```

#### ApprovalCard
```
Component name: ApprovalCard
Frame: Auto Layout Vertical, radius/md, border 1px neutral/200, shadow/sm
Background: white

Sections:
  Header (padding 14px 16px, border-bottom)
    Left: Avatar + Name + Meta (employee name, mission ID, dates)
    Right: StatusPill
    
  Body (padding 14px 16px, 4-column grid)
    Slot fields: Mission Type | Destination | Duration | Amount
    
  Footer (padding 10px 16px, bg surface/table-head, border-top)
    Right-aligned: [Reject Button] [Approve Button]
    Optional: Note textarea (shown on Reject click)

Variants:
  type = LineManager    (shows LM role label in avatar area)
  type = DivisionManager
```

#### FormField
```
Component name: FormField
Frame: Auto Layout Vertical, gap 4px, width 100%

Sub-elements:
  Label    11px/600/Inter, neutral/500, uppercase, letter-spacing 0.5px
  Input    height 36px, border 1px neutral/300, radius/sm, padding 0 10px
           font 12.5px/400/Inter, neutral/700
           focus: border color/brand/primary-dark, shadow/focus-yellow
  Helper   11px/400/Inter, neutral/400 (neutral info) or semantic/danger (error)

Variants:
  type = text
  type = select   (chevron icon right, appearance none)
  type = date
  type = textarea  (height 80px min)
  type = file-upload (dashed border, drag area)
  
States: default / focused / filled / error / disabled / read-only
```

#### DataTable
```
Component name: DataTable
Frame: Auto Layout Vertical, radius/md, border 1px neutral/200, overflow hidden
Background: white

Sub-components:
  TableHeader  bg surface/table-head, padding 10px 16px
               font 11px/600/Inter, neutral/400, uppercase, letter-spacing 0.5px
               border-bottom 1px neutral/200
               
  TableRow     padding 12px 16px, border-bottom 1px neutral/50
               hover state: bg surface/row-hover
               font 12.5px/400/Inter, neutral/700
               
  TableFooter  pagination controls: [← Prev] [1][2][3][...] [Next →]
               font 12px/500, secondary button style

Column types:
  text, amount (mono font, right-align), status (StatusPill), date, action-link
```

#### Sidebar
```
Component name: Sidebar
Frame: Fixed width 240px, height fill, bg surface/sidebar (#0F0F0F)
Auto Layout Vertical

Logo Area    padding 20px 20px 16px
             MTN badge: bg brand/primary, font 13px/800, border-radius 40px
             System name: 11px/400, rgba(255,255,255,0.45)
             border-bottom: 1px rgba(255,255,255,0.06)

Nav Body     flex 1, padding 12px 0, overflow-y auto

  NavSection  margin-bottom 4px
    GroupLabel   9px/600, rgba(255,255,255,0.25), uppercase, letter-spacing 1.5px
                 padding 8px 20px 4px

    NavItem      padding 9px 20px, gap 10px
                 font 12.5px/400, rgba(255,255,255,0.55)
                 icon: 16px tabler-icon, same color
                 
                 State active:
                   bg rgba(255,203,0,0.10)
                   text color/brand/primary
                   left border: 3px solid brand/primary
                   
                 State hover:
                   bg rgba(255,255,255,0.04)
                   text rgba(255,255,255,0.85)
                   
                 Badge slot: bg brand/primary, text black, 10px/700, radius/full

Nav Sections (matching requirements navigation menu exactly):
  [No group label]
    Dashboard           icon: dashboard
    
  MISSION MANAGEMENT
    Mission List        icon: list
    Create Mission      icon: plus-circle
    My Missions         icon: user-check
    
  APPROVALS
    Pending Approvals   icon: clock + badge (count)
    
  TRAVEL REVIEW
    Travel Cost Review  icon: map-pin
    
  TREASURY
    Payments            icon: credit-card
    
  MISSION CLOSURE
    Mission Closure     icon: flag-check
    Mission Extensions  icon: arrows-maximize
    
  FINANCE
    Settlements         icon: calculator
    
  REPORTS
    Employee History    icon: report
    Debit / Credit      icon: balance

Bottom Area   padding 16px 20px, border-top 1px rgba(255,255,255,0.06)
  Avatar + user name + role label

User footer variants:
  role = Assigned Person
  role = Line Manager
  role = Division Manager
  role = Travel Team
  role = Treasury
  role = Finance
  role = HR
```

#### Topbar
```
Component name: Topbar
Frame: height 64px, bg white, border-bottom 1px neutral/200
Auto Layout Horizontal, padding 0 24px, gap 12px, align center

Left slot:   Page title — font 17px/600/Space Grotesk, neutral/900
Right slot:  CTA Button (context-specific, Primary variant)
             Search input (optional, 280px wide)
             User avatar (32px, initials badge)
```

---

## 2.4 FIGMA PAGE HIERARCHY & FRAME STRUCTURE

### Page 4 — Screens: Mission Management
```
Frame: Dashboard              1440 × 900
Frame: Mission_List           1440 × 900
Frame: Create_Mission         1440 × 900
Frame: My_Missions            1440 × 900
Frame: Mission_Details        1440 × 1100
```

### Page 5 — Screens: Approvals & Review
```
Frame: Pending_Approvals      1440 × 900
Frame: Travel_Cost_Review     1440 × 900
```

### Page 6 — Screens: Operations
```
Frame: Payments               1440 × 900
Frame: Mission_Extensions     1440 × 900
Frame: Mission_Closure        1440 × 900
```

### Page 7 — Screens: Finance & Reports
```
Frame: Settlements            1440 × 900
Frame: Employee_Mission_History   1440 × 900
Frame: Debit_Credit_Report    1440 × 900
```

---

## 2.5 AUTO LAYOUT STRUCTURE — PAGE SHELL

Every screen uses this base template:

```
[Frame: ScreenName]  1440 × 900
  Auto Layout: Horizontal, gap 0

  [Frame: Sidebar]   240 × 900   — component instance: Sidebar
  
  [Frame: MainArea]  1200 × 900
    Auto Layout: Vertical, gap 0
    
    [Frame: Topbar]   1200 × 64   — component instance: Topbar
    
    [Frame: PageBody]  1200 × 836
      Auto Layout: Vertical, gap space/section-gap (20px)
      Padding: 24px all sides
      Background: color/surface/page (#F2F4F7)
      Overflow: vertical scroll
      
      [Content sections...]
```

---

# 2.6 SCREEN SPECIFICATIONS

---

## SCREEN 01 — DASHBOARD

```
Frame Name:     Dashboard
Frame Size:     1440 × 900
Primary User:   All Roles (view varies by role)
Nav Active:     Dashboard
Topbar Title:   "Dashboard"
Topbar CTA:     [+ New Mission Request]  (hidden for non-Assigned Person roles)
```

### Layout Structure
```
PageBody (Auto Layout Vertical, gap 20px)
  └── KPI Row          (Auto Layout Horizontal, gap 14px)
  └── Table Section    (Auto Layout Vertical, gap 12px)
      └── Section Title
      └── DataTable
  └── Quick Actions    (Auto Layout Horizontal, gap 12px)
```

### Sections

**Section A — KPI Cards Grid**
```
Container: 4-column grid, gap 14px, width 100%

KPICard 1:
  value: [dynamic: total open missions]
  label: "Open Missions"
  icon: ti-map-pin

KPICard 2:
  value: [dynamic: pending approvals count]
  label: "Pending Approvals"
  icon: ti-clock
  variant: highlighted (if count > 0)

KPICard 3:
  value: [dynamic: missions active today]
  label: "Active Today"
  icon: ti-check-circle

KPICard 4:
  value: [dynamic: pending payments]
  label: "Pending Payments"
  icon: ti-credit-card
```

**Section B — My Recent Missions** *(shown to Assigned Person role)*
```
Section header: "My Recent Missions"  font 14px/600, neutral/900
DataTable:
  Columns: Mission ID | Destination | Start Date | End Date | Status | Action
  Max rows: 5 (+ View All link)
  Action column: [View Details] text link, info color
```

**Section C — Pending Actions** *(role-specific)*
```
Role = Line Manager / Division Manager:
  Section header: "Pending Approvals"
  DataTable (compact): Mission ID | Employee | Submitted | Days Waiting | Action
  Action: [Approve / Review] button

Role = Travel Team:
  Section header: "Missions Awaiting Cost Review"
  DataTable: Mission ID | Employee | Destination | Type | Action

Role = Treasury:
  Section header: "Approved for Payment"
  DataTable: Mission ID | Employee | Amount | Approved Date | Action

Role = Finance:
  Section header: "Missions Pending Settlement"
  DataTable: Mission ID | Employee | Closed Date | Amount | Action
```

### Fields
No input fields on Dashboard. Read-only display only.

### Actions
- [+ New Mission Request] → navigate to Create_Mission
- [View Details] → navigate to Mission_Details
- [Approve / Review] → navigate to Pending_Approvals

---

## SCREEN 02 — MISSION LIST

```
Frame Name:     Mission_List
Frame Size:     1440 × 900
Primary User:   Assigned Person (and managers/admin viewing all)
Nav Active:     Mission List
Topbar Title:   "Mission List"
Topbar CTA:     [+ New Mission Request]
```

### Layout Structure
```
PageBody
  └── FilterBar
  └── DataTable (full width)
  └── Pagination
```

### Sections

**Section A — Filter Bar**
```
Container: Auto Layout Horizontal, gap 10px, padding 12px 16px
Background: white, radius/md, shadow/sm, border 1px neutral/200

Fields:
  Search input       placeholder "Search by mission ID, employee name..."  width 280px
  Select: Status     options: All / Draft / Pending LM / Pending DM / Pending Travel
                              / Pending Payment / Active / Extended / Closed
                              / Pending Settlement / Completed / Rejected
  Select: Type       options: All / National / International
  Date range picker  label "Date Range"  (two date inputs: From / To)
  [Search] button    Primary variant
  [Clear] button     Ghost variant
```

**Section B — Data Table**
```
DataTable columns:
  Mission ID    120px   font mono/600, info color, clickable link
  Employee      180px   text
  Destination   160px   text
  Type          100px   StatusPill (or plain text: National/International)
  Start Date    120px   date format DD/MM/YYYY
  End Date      120px   date format DD/MM/YYYY
  Days          70px    numeric, right-align
  Amount        130px   numeric with currency, mono font, right-align
  Status        150px   StatusPill component
  Actions       100px   [View] icon button

Table settings:
  Sortable columns: Mission ID, Employee, Start Date, Status
  Row hover: bg surface/row-hover
  Empty state: illustration + "No missions found" + subtext
```

### Actions
- Row click OR [View] → navigate to Mission_Details
- [+ New Mission Request] → navigate to Create_Mission

---

## SCREEN 03 — CREATE MISSION

```
Frame Name:     Create_Mission
Frame Size:     1440 × 900 (body scrolls)
Primary User:   Assigned Person
Nav Active:     Create Mission
Topbar Title:   "New Mission Request"
Topbar CTA:     none (actions in form footer)
```

### Layout Structure
```
PageBody
  └── AlertBanner (business rule: "You may not have more than one open mission at a time.")
  └── FormCard (white card, full width, radius/md, shadow/sm, padding 24px)
      └── Form Sections (Auto Layout Vertical, gap 20px)
          └── Section: Mission Information
          └── Section: Travel Details
          └── Section: Per Diem Calculation Preview
          └── FormFooter
```

### Form Sections

**Section: Mission Information**
```
Section label: "Mission Information"  font 13px/600, neutral/700, border-bottom 1px neutral/200, padding-bottom 8px mb 16px

Grid: 2-column, gap 14px

Row 1:
  FormField  label="Mission Type"  type=select  required
             options: National | International
  FormField  label="Assigned Person"  type=text  read-only (auto-populated from logged-in user)

Row 2:
  FormField  label="Mission Start Date"  type=date  required
  FormField  label="Mission End Date"    type=date  required

Row 3:
  FormField  label="Number of Days"  type=text  read-only  (auto-calculated from dates)
  FormField  label="Destination"     type=select  required
             options: [populated from configurable destination list]

Row 4 (full width):
  FormField  label="Notes"  type=textarea  rows=3  placeholder="Optional remarks..."
```

**Section: Travel Details**
```
Section label: "Travel Details"  same style as above

Grid: 2-column, gap 14px

Row 1:
  FormField  label="Amount Per Day"   type=text  required  
             helper="Auto-suggested based on mission type and destination"
  FormField  label="Currency"         type=text  read-only
             value auto-set: National → local currency | International → foreign currency

Row 2 (full width):
  CalcPreviewRow container — bg #F9FAFB, radius/sm, border 1px neutral/200, padding 12px 16px
  
  Rows:
    "Amount Per Day"        [value]
    "× Number of Days"      [value]
    "Per Diem Subtotal"     [calculated]
    "Accommodation"         [value]    (if applicable)
    ─────────────────────────────────
    "Total Estimated Amount"  [bold, 14px/700, neutral/900]  [calculated total]
    "Currency"              [local or foreign]
```

**Form Footer**
```
Container: Auto Layout Horizontal, justify space-between, padding 16px 24px
Border-top: 1px neutral/200, bg white

Left:   [← Cancel] Ghost button  → navigate to Mission_List
Right:  [Save as Draft]  Secondary button
        [Submit Request]  Primary button  → triggers workflow → status = Pending LM
```

### Business Rule Notes (inline in Figma)
```
RULE: Employee cannot have more than one open mission.
  → Show AlertBanner at top if employee already has open mission.
  → Disable [Submit Request] button.
  → AlertBanner text: "You currently have an open mission (ID: TRV-XXXX). You cannot submit a new request until it is completed or cancelled."
  → AlertBanner type: warning

RULE: Mission Type drives Currency field automatically.
RULE: Number of Days is calculated, not manually entered.
RULE: Total Estimated Amount is calculated, not manually entered.
```

---

## SCREEN 04 — MY MISSIONS

```
Frame Name:     My_Missions
Frame Size:     1440 × 900
Primary User:   Assigned Person
Nav Active:     My Missions
Topbar Title:   "My Missions"
Topbar CTA:     [+ New Mission Request]
```

### Layout Structure
```
PageBody
  └── FilterBar (simplified: Status filter + Date range only)
  └── DataTable
```

### Sections

**Filter Bar**: Status dropdown (all statuses) + Date Range From/To + [Search] + [Clear]

**Data Table columns**:
```
Mission ID    mono, clickable link
Destination
Type          National / International
Start Date
End Date
Days
Amount        mono, right-align
Status        StatusPill
Actions       [View Details] | [Close Mission]*  | [Extend]*  | [Cancel]*

* = conditionally shown based on current status
```

**Conditional Action Rules**:
```
[Close Mission]   shown only when status = Mission Active OR Mission Extended
[Extend Mission]  shown only when status = Mission Active
[Cancel]          shown only when status = Draft
[View Details]    always shown
```

---

## SCREEN 05 — MISSION DETAILS

```
Frame Name:     Mission_Details
Frame Size:     1440 × 1100  (scrollable body)
Primary User:   All roles (read-only view; action buttons vary by role)
Nav Active:     (inherits from origin)
Topbar Title:   Mission ID  e.g. "TRV-2024-0042"
Topbar CTA:     Role-contextual (see below)
```

### Layout Structure
```
PageBody (Auto Layout Vertical, gap 20px)
  └── WorkflowTracker (full width card)
  └── Two-column grid (2fr 1fr gap 20px)
      └── Left column (Auto Layout Vertical, gap 16px)
          └── MissionInfoCard
          └── TravelDetailsCard
          └── ExtensionHistoryCard  (shown if status ≥ Extended)
          └── ClosureDocumentsCard  (shown if status ≥ Closed)
          └── SettlementCard        (shown if status = Completed)
      └── Right column (Auto Layout Vertical, gap 16px)
          └── StatusHistoryCard
          └── ApprovalTrailCard
```

### WorkflowTracker Card
```
Background: white, radius/md, shadow/sm, border 1px neutral/200
Padding: 16px 20px
WorkflowTracker component (9 steps per confirmed workflow)
```

### MissionInfoCard
```
Card header: "Mission Information"  + StatusPill (current status, right-aligned)
Card body (4-column info grid):
  Mission ID | Assigned Person | Mission Type | Destination
  Start Date | End Date        | Duration     | Currency
  
Notes section (if present): italic, neutral/500
```

### TravelDetailsCard
```
Card header: "Travel Details"
Body (2-col):
  Per Diem Rate | Accommodation
  Subtotal      | Total Approved Amount
  Currency      | Payment Status
```

### StatusHistoryCard
```
Card header: "Status History"
List of status change entries (Auto Layout Vertical):
  Each entry:
    Icon (circle, color matches status)
    Status label  (bold 12px)
    Changed by    (12px neutral/500)
    Timestamp     (11px neutral/400)
    Note (if any) (italic 11px neutral/500)
```

### ApprovalTrailCard
```
Card header: "Approval Trail"
Table:
  Stage | Actioned By | Decision | Date | Notes
  
Stages shown:  Line Manager | Division Manager | Travel Team | Treasury
```

### Contextual CTAs (Topbar Right)
```
Role = Assigned Person + status = Draft:
  [Edit Mission]  [Submit for Approval]  [Cancel Request]

Role = Assigned Person + status = Active:
  [Extend Mission]  [Close Mission]

Role = Line Manager + status = Pending LM:
  → redirect to Pending_Approvals screen

Role = Division Manager + status = Pending DM:
  → redirect to Pending_Approvals screen

Role = Travel Team + status = Pending Travel:
  → redirect to Travel_Cost_Review screen

Role = Treasury + status = Pending Payment:
  → redirect to Payments screen

Role = Finance + status = Pending Settlement:
  → redirect to Settlements screen

Role = Any + status = Completed / Rejected:
  No action buttons (read-only)
```

---

## SCREEN 06 — PENDING APPROVALS

```
Frame Name:     Pending_Approvals
Frame Size:     1440 × 900
Primary User:   Line Manager, Division Manager
Nav Active:     Pending Approvals
Topbar Title:   "Pending Approvals"
Topbar CTA:     none
```

### Layout Structure
```
PageBody
  └── FilterBar (Mission Type filter + Search by employee name)
  └── ApprovalCards list (Auto Layout Vertical, gap 14px)
```

### ApprovalCard Fields
```
Header:
  Left:  Avatar (initials) + Employee Full Name + Employee ID
  Right: StatusPill (Pending LM or Pending DM depending on approver role)
  
Body (4-column):
  Mission Type    Destination    Start Date    End Date
  Days            Amount         Currency      Submitted Date
  
Notes area (below body):
  Mission Notes text (if submitted by employee)
  
Footer:
  Left:  [View Full Details] Ghost button → Mission_Details
  Right: [Reject] Danger-outline button + [Approve] Success button
```

### Reject Flow
```
On [Reject] click:
  Inline expansion: textarea appears below footer
  Label: "Rejection Reason (required)"
  Placeholder: "Provide a reason for rejection..."
  Buttons: [Cancel] [Confirm Rejection]
  
  On confirm:
    Status → Rejected
    Rejection note saved to status history
```

### Approve Flow
```
On [Approve] click:
  Inline confirmation (no modal): "✓ Approved — mission advanced to [next stage]"
  ApprovalCard collapses / removed from list
  
  Line Manager approval → status = Pending DM
  Division Manager approval → status = Pending Travel
```

### Empty State
```
Icon: ti-circle-check (large, neutral/300)
Title: "No pending approvals"
Subtext: "All missions have been reviewed."
```

---

## SCREEN 07 — TRAVEL COST REVIEW

```
Frame Name:     Travel_Cost_Review
Frame Size:     1440 × 900
Primary User:   Travel Team
Nav Active:     Travel Cost Review
Topbar Title:   "Travel Cost Review"
Topbar CTA:     none
```

### Layout Structure
```
PageBody
  └── FilterBar (search + date range)
  └── MissionReviewList (Auto Layout Vertical, gap 14px)
      [For each mission pending travel review:]
      └── ReviewCard
```

### ReviewCard Fields
```
Card Header:
  Mission ID  |  Employee Name  |  Submitted Date  |  StatusPill (Pending Travel)
  
Card Body (2-column):
  Left: Read-only Mission Info
    Mission Type | Destination | Start Date | End Date
    Duration | Employee Notes
    
  Right: Travel Cost Entry Form (editable)
    FormField  label="Per Diem Rate"       type=text  required
    FormField  label="Accommodation Cost"  type=text
    FormField  label="Other Expenses"      type=text
    FormField  label="Currency"            type=select  (National/International)
    
    CalcPreview:
      Per Diem × Days = Subtotal
      + Accommodation
      + Other
      ──────────────────────────
      Total Travel Amount:  [bold]
      
    FormField  label="Travel Team Notes"   type=textarea  optional

Card Footer:
  [Send to Treasury] Primary button  → status = Pending Payment
  [Return to Submitter] Secondary button  (with note textarea)
```

**NOTE**: No "Submit to Finance GL" button. Final action is "Send to Treasury."

---

## SCREEN 08 — PAYMENTS

```
Frame Name:     Payments
Frame Size:     1440 × 900
Primary User:   Treasury
Nav Active:     Payments
Topbar Title:   "Payments"
Topbar CTA:     none
```

### Layout Structure
```
PageBody
  └── Summary KPI row (3 cards: Total Pending | Total Amount | Oldest Pending)
  └── FilterBar (search + date range + mission type)
  └── DataTable
```

### KPI Row (3 cards)
```
KPICard: "Missions Pending Payment"  value = count
KPICard: "Total Amount Pending"      value = sum with currency
KPICard: "Oldest Pending (Days)"     value = max days waiting
```

### Data Table Columns
```
Mission ID    mono/info, link
Employee      text
Destination   text
Type          National / International
Amount        mono, right-align, bold
Currency      text
Travel Review Date   date
Days Pending   numeric
Actions:  [Process Payment]  Primary-sm button
```

### Payment Processing Panel
```
Triggered by [Process Payment] → inline expansion or right-panel (side sheet, 400px):

Panel title: "Process Payment — [Mission ID]"

Display (read-only):
  Employee Name | Mission Type | Destination
  Duration      | Amount       | Currency

FormField  label="Payment Reference / Voucher No."  type=text  required
FormField  label="Payment Date"                     type=date  required  default today
FormField  label="Treasury Notes"                   type=textarea  optional

Footer:
  [Cancel] Secondary
  [Confirm Payment]  Primary  → status = Mission Active
```

---

## SCREEN 09 — MISSION EXTENSIONS

```
Frame Name:     Mission_Extensions
Frame Size:     1440 × 900
Primary User:   Assigned Person (request), then approval chain
Nav Active:     Mission Extensions
Topbar Title:   "Mission Extensions"
Topbar CTA:     none
```

### Layout Structure
```
PageBody
  └── FilterBar
  └── ExtensionList (DataTable format)
  └── [When "Request Extension" triggered from My Missions:] Extension Request Form (card)
```

### Extension Request Form
```
FormCard header: "Request Mission Extension — [Mission ID]"

Read-only display row:
  Original Start Date | Original End Date | Original Duration | Current Status

Form fields:
  FormField  label="New End Date"           type=date  required
             validation: must be after current end date
  FormField  label="Extension Duration (Days)"  type=text  read-only (calculated)
  FormField  label="Reason for Extension"   type=textarea  required

CalcPreview:
  Original Amount:        [amount]
  Extension Days × Rate:  [calculated]
  ─────────────────────────────────────
  New Total Amount:       [bold]

Footer:
  [Cancel] Ghost
  [Submit Extension Request] Primary → re-enters approval chain:
    status = Pending LM → Pending DM → Pending Travel → Pending Payment → Mission Extended
```

### Extension List Table
```
Columns:
  Mission ID | Employee | Original End | New End | Extension Days | Reason | Status | Actions

Extension-specific statuses use same StatusPill component:
  Pending LM / Pending DM / Pending Travel / Pending Payment / Mission Extended
```

---

## SCREEN 10 — MISSION CLOSURE

```
Frame Name:     Mission_Closure
Frame Size:     1440 × 900
Primary User:   Assigned Person
Nav Active:     Mission Closure
Topbar Title:   "Mission Closure"
Topbar CTA:     none
```

### Layout Structure
```
PageBody
  └── FilterBar (shows missions with status = Active or Extended for current user)
  └── ClosureList (DataTable)
  └── ClosureForm (expandable card, or navigate to detail page)
```

### Closure Form
```
FormCard header: "Close Mission — [Mission ID]"

Read-only summary:
  Employee | Destination | Start Date | End Date | Status | Amount Paid

Form fields:
  FormField  label="Actual Return Date"     type=date  required
  FormField  label="Actual Days Spent"      type=text  read-only (calculated)
  
  Section: "Supporting Documents"
    FormField  label="Attachments"  type=file-upload
               helper="Upload receipts, reports, or supporting documents"
               accepts: PDF, JPG, PNG
               multiple files allowed
               
  FormField  label="Closure Notes"  type=textarea  optional

Footer:
  [Cancel]
  [Submit Closure] Primary → status = Mission Closed → status = Pending Settlement
```

---

## SCREEN 11 — SETTLEMENTS

```
Frame Name:     Settlements
Frame Size:     1440 × 1100 (scrollable)
Primary User:   Finance
Nav Active:     Settlements
Topbar Title:   "Settlements"
Topbar CTA:     none
```

### Layout Structure
```
PageBody
  └── FilterBar
  └── SettlementList (DataTable of missions pending settlement)
  └── [On row select:] SettlementDetailPanel (below table or side panel)
```

### Settlement List Table
```
Columns:
  Mission ID | Employee | Destination | Closed Date | Amount Paid | Days | Status | Actions
  
Actions: [Process Settlement] Primary-sm
```

### Settlement Detail Panel
```
Panel header: "Settle Mission — [Mission ID]"

Two-column layout (2fr 1fr):

Left — Settlement Table:
  Table headers: Category | Planned | Actual | Difference
  
  Rows:
    Per Diem            [planned]  [actual: from closure docs]   [diff]
    Accommodation       [planned]  [actual]                      [diff]
    Other Expenses      [planned]  [actual]                      [diff]
    ─────────────────────────────────────────────────────────────────
    Total               [planned]  [actual]                      [diff]
    Amount Already Paid [paid]
    ─────────────────────────────────────────────────────────────────
    Balance             
    
  FormField  label="Finance Notes"   type=textarea  optional
  FormField  label="Settlement Reference"  type=text  required

Right — Balance Card:
  SettlementBalanceCard component
  
  If balance > 0 (employee owes back):
    bg: danger-bg, text: danger
    Label: "Employee owes company"
    Amount: [+ amount, bold]
    
  If balance < 0 (company owes employee):
    bg: success-bg, text: success
    Label: "Company owes employee"
    Amount: [amount, bold]
    
  If balance = 0 (settled):
    bg: neutral/100, text: neutral/700
    Label: "No balance due"
    Amount: 0.00

[Process Settlement] button → status = Completed
```

**NOTE**: Finance is the final step that completes the mission. No Travel Team approval of settlement. No additional steps after Finance confirms.

---

## SCREEN 12 — EMPLOYEE MISSION HISTORY REPORT

```
Frame Name:     Employee_Mission_History
Frame Size:     1440 × 900
Primary User:   Finance
Nav Active:     Employee History
Topbar Title:   "Employee Mission History"
Topbar CTA:     [Export to Excel]
```

### Layout Structure
```
PageBody
  └── ReportFilterBar
  └── DataTable (report format)
```

### Report Filter Bar
```
FormField  label="Employee"  type=select  (searchable dropdown of all employees)
FormField  label="From Date"  type=date
FormField  label="To Date"    type=date
FormField  label="Mission Type"  type=select  (All / National / International)
FormField  label="Status"        type=select  (All / Completed / Active / Rejected / etc.)
[Generate Report] Primary
[Export to Excel] Secondary
```

### Report Table Columns
```
Mission ID  | Mission Type | Destination | Start Date | End Date | Days | 
Amount Paid | Settlement Amount | Balance | Final Status
```

### Report Summary Row (pinned at table bottom)
```
Background: neutral/100, font bold
  Total Missions: [count]
  Total Days: [sum]
  Total Amount Paid: [sum]
  Total Settled: [sum]
  Net Balance: [sum]
```

---

## SCREEN 13 — DEBIT / CREDIT REPORT

```
Frame Name:     Debit_Credit_Report
Frame Size:     1440 × 900
Primary User:   Finance
Nav Active:     Debit / Credit
Topbar Title:   "Debit / Credit Report"
Topbar CTA:     [Export to Excel]
```

### Layout Structure
```
PageBody
  └── ReportFilterBar
  └── Summary cards (3 KPIs)
  └── DataTable
```

### Filter Bar
```
FormField  label="From Date"  type=date
FormField  label="To Date"    type=date
FormField  label="Employee"   type=select  optional
[Generate Report]  [Export to Excel]
```

### Summary KPIs
```
KPICard: "Total Debit (Employee Owes)"   value = sum, text color danger
KPICard: "Total Credit (Company Owes)"  value = sum, text color success
KPICard: "Net Balance"                  value = net, color = danger (if negative) / success (if positive)
```

### Report Table Columns
```
Employee Name | Employee ID | Mission ID | Mission Type | Amount Paid | 
Actual Amount | Debit | Credit | Balance | Status
```

---

# 2.7 WORKFLOW STATUS MACHINE (for Figma Prototype Flows)

```
[Draft]
  ├── [Submit] → Pending Line Manager Approval
  └── [Cancel] → (deleted / no status)

[Pending Line Manager Approval]
  ├── [LM Approve]  → Pending Division Manager Approval
  └── [LM Reject]   → Rejected

[Pending Division Manager Approval]
  ├── [DM Approve]  → Pending Travel Review
  └── [DM Reject]   → Rejected

[Pending Travel Review]
  ├── [Travel Submit] → Pending Payment
  └── [Travel Return] → Pending Line Manager Approval  (resubmit)

[Pending Payment]
  ├── [Treasury Confirm] → Mission Active
  └── (no reject — Treasury only confirms)

[Mission Active]
  ├── [Assigned Person: Extend] → Extension sub-flow:
  │     Pending LM → Pending DM → Pending Travel → Pending Payment → Mission Extended
  └── [Assigned Person: Close] → Mission Closed → Pending Settlement

[Mission Extended]
  └── [Assigned Person: Close] → Mission Closed → Pending Settlement

[Mission Closed / Pending Settlement]
  └── [Finance: Settle] → Completed

[Completed]  ← TERMINAL STATE (no further actions)
[Rejected]   ← TERMINAL STATE (no further actions)
```

---

# 2.8 FIGMA PROTOTYPE CONNECTIONS (Page 8)

```
Flow 1: Mission Creation
  Dashboard → [+ New Mission] → Create_Mission → [Submit] → Mission_List

Flow 2: Approval Chain
  Pending_Approvals → [Approve] → (card removed) → Dashboard
  Pending_Approvals → [Reject] → (inline rejection note) → Dashboard

Flow 3: Travel Review
  Travel_Cost_Review → [Send to Treasury] → Payments

Flow 4: Payment
  Payments → [Process Payment] → Mission_Details (status = Active)

Flow 5: Extension
  My_Missions → [Extend] → Mission_Extensions → (re-enters approval chain)

Flow 6: Closure
  My_Missions → [Close] → Mission_Closure → [Submit Closure] → Settlements

Flow 7: Settlement
  Settlements → [Process Settlement] → Mission_Details (status = Completed)
```

---

# 2.9 HANDOFF NOTES (Page 9)

## Navigation Consistency
- Sidebar component is shared across ALL screens
- Active nav item changes per screen (use Figma component properties)
- Badge count on "Pending Approvals" nav item = live count from backend

## Role-Based Visibility
- Topbar CTA and table action columns are variant-driven by role property
- Use Figma component variants for role switching in prototype
- Recommended: add a role switcher in prototype for reviewer demonstrations

## Status Pill Usage
- Never deviate from the 11 defined statuses
- Colors are fixed per status — do not use ad hoc colors
- Statuses not in requirements = do not create

## Forms
- All calculated fields (Days, Total Amount) are read-only in Figma frames
- Required fields marked with asterisk (*) after label
- Inline validation error states built as component variants

## Currency Logic
- National mission → local currency field auto-populated, not editable
- International mission → foreign currency field auto-populated, not editable
- This drives the CalcPreview amounts

## File Uploads (Mission Closure)
- Figma shows the upload zone as a dashed-border FormField
- In prototype, treat as a static state (uploaded = 3 files shown as chips)

## Empty States
- Every DataTable has an empty state variant
- Every ApprovalCard list has an empty state
- Empty states use: illustration placeholder + primary message + secondary description

## Scrolling
- Mission_Details frame: body scrolls vertically (PageBody frame = fill height with overflow scroll)
- Settlements: Settlement Detail Panel scrolls independently
- Sidebar: scrollable nav if nav items exceed viewport height

## Removed Items (DO NOT Re-Add)
- ❌ Archived status / Archived (Rejected) screen
- ❌ Finance GL step in workflow
- ❌ HR Absence logging step
- ❌ System notification module
- ❌ "Submit to Finance GL" button
- ❌ Audit log module
- ❌ Administration / configuration module
- ❌ KPI trend delta indicators on dashboard

---

*End of MTN Sudan Travel System — Figma Production Specification*
*Prepared from: Travel_System_Requirements.docx (source of truth)*
*Version: 1.0 — Compliant with all 10 known corrections*
