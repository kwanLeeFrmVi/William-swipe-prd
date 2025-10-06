# Product Requirements Document: "Are You Spending Smart?" Swipe Game

## Overview

A Tinder-style swipe game for financial awareness. Users review past transactions and categorize them as "Necessary" or "Unnecessary" through an engaging swipe interface.

**Platform:** ReactJS web application (mobile-first, responsive)

---

## Visual Reference


https://github.com/user-attachments/assets/0e05b762-dd9b-4cda-b44f-09007f9889a0


Use the screenshots from the provided video to illustrate each screen and interaction state.

---

## User Flow

1. **Welcome Screen** → Tap time period dropdown → **Time Period Modal** appears → Select period → Tap SELECT
2. Tap START → **Game Screen** → Swipe through transactions → Categorize each one
3. **Results Screen (Swipe Score)** → View savings amount, score cards, Power Moves insights, and list of unnecessary transactions → Done


---

## Screen Specifications

### 1. Welcome Screen

<img height="450" alt="image" src="https://github.com/user-attachments/assets/da492e2c-17ab-4cd6-b722-20bb696cc4f4" />

**Elements:**
- **Title:** "ARE YOU SPENDING SMART? 🧠"
  - "ARE YOU" (white) / "SPENDING" (orange #FF8C42) / "SMART?" (white)
- **Instructions:** "Swipe through your past transactions. Mark the ones that are unnecessary and the ones you needed."
- **Preview Card:** Sample transaction card
- **Time Period Dropdown:** Options: 7 Days, 30 Days, 90 Days, 1 Year, Custom
- **START Button:** Light blue (#5DADE2), full width

**Background:** Dark blue gradient (#1E3A5F to #2C5F8D)

---

### 1.5 Time Period Selection Modal

<img height="450" alt="2025-10-06_15-03-56" src="https://github.com/user-attachments/assets/4e39da5e-541f-47f2-8545-5a69e76af2e1" />


This modal appears when user taps the "Select Time Period" dropdown on the Welcome Screen.

**Modal Design:**
- White rounded modal overlay
- Semi-transparent dark background (backdrop)
- Centered on screen

**Modal Header:**
- "Select Time Period" (dark text, left-aligned)

**Options List:**
- Scrollable picker/list of options
- Options: "7 Days", "14 Days", "30 Days", "90 Days", "1 Year"
- Selected option highlighted/centered
- Scroll wheel style picker (iOS style)

**Select Button:**
- Light blue button (#5DADE2)
- White text: "SELECT"
- Full width within modal
- Bottom of modal

**Interaction:**
- User scrolls to select desired time period
- Taps "SELECT" to confirm and close modal
- Tapping outside modal closes it without selection
- Selected value updates the dropdown on Welcome Screen

---

### 2. Game Screen

<img height="450" alt="image" src="https://github.com/user-attachments/assets/4b24d8b7-62df-4f42-b88f-61ea0fba1211" />

**Progress Indicator (Top):**
- Horizontal row of 10 segments
- Completed: Orange (#FF8C42)
- Remaining: Dark blue/gray

**Transaction Card (Center):**
- White rounded card with shadow
- Merchant name (top)
- Company logo (centered)
- Category badge (icon + text, gray pill)
- Dollar amount (large, bold, e.g., "$149.00")
- Date (bottom, gray text)

**Swipe Indicators:**
- **Left:** Red triangle/arrow (Unnecessary)
- **Right:** Green triangle/arrow with amount (Necessary)
- Card tilts in drag direction

<img width="1080" height="1920" alt="image" src="https://github.com/user-attachments/assets/f5a86390-d5e9-46be-bfe6-85dc03ebb265" />


<img height="450" alt="image" src="https://github.com/user-attachments/assets/c3c1bd58-3802-4387-9dca-522cb1e99f9d" />

<img height="450" alt="image" src="https://github.com/user-attachments/assets/9d2d098d-73f6-4d1a-aa43-ec16022fe8fe" />

<img height="450" alt="image" src="https://github.com/user-attachments/assets/0709686c-a741-4e1a-8151-61681bf5a71f" />


**Action Buttons (Bottom):**
- **Left (Red #E74C3C):** Thumbs down icon, "Unnecessary" label
- **Right (Green #2ECC71):** Thumbs up icon, "Necessary" label

---

### 3. Results Screen
<img height="450" alt="2025-10-06_15-05-36" src="https://github.com/user-attachments/assets/d3009821-283f-466e-9774-e993bec53f36" />

<img height="450" alt="image" src="https://github.com/user-attachments/assets/285af557-fae9-4423-873a-2db15a68a067" />

**Header:**
- "Your Swipe Score 🎯" (white text, centered)

**Savings Summary:**
- "You could have saved" (white text)
- Large dollar amount (e.g., "$439") - huge, bold, white text
- This shows total unnecessary spending

**Score Cards (Side by Side):**
- **Left Card (Red):**
  - Number of unnecessary transactions (e.g., "8")
  - "UNNECESSARY" label with X icon
  - Red background (#E74C3C)
  
- **Right Card (Green):**
  - Number of necessary transactions (e.g., "17")
  - "NECESSARY" label with checkmark icon
  - Green background (#2ECC71)

**Power Moves Section:**
- Section header: "Power Moves"
- List of 3 actionable insights, each with:
  - Orange square icon with emoji (🔥, ✨, 🚀)
  - Bold title (e.g., "Smash your car loan")
  - Description text showing impact of saving money
  - Examples:
    - "If you redirected $439/week you could"
    - "Save $10,014 on interest and finish your loan 1 year 4 months faster"
    - "Reach your goal in 1 year 5 months Vs 2 years 4 months"

**List of Unnecessary Spend:**
- Section header: "List of Unnecessary Spend" (white text, left-aligned)
- Scrollable list of white rounded cards
- Each card shows:
  - Company logo (left, circular or square)
  - Merchant name (bold, black)
  - Category text (gray, smaller)
  - Dollar amount (right, bold, black)
  - White background, full width with spacing

**Interactions:**
- Entire screen is scrollable
- Power Moves cards may be tappable for more details (optional)
- Scroll to see complete list of unnecessary transactions

**Background:** Dark blue gradient (same as other screens)

**Bottom Actions (if any):**
- May include "Create Budget" or "Done" button at bottom
- Or user swipes down/back to exit

---

## Interactions

### Swipe Mechanics
- **Swipe Left:** Card flies off left, marked "Unnecessary"
- **Swipe Right:** Card flies off right, marked "Necessary"
- **Threshold:** 100px drag distance
- **Insufficient swipe:** Card snaps back to center
- **Card tilt:** Proportional to drag distance

### Button Taps
- Left button = Swipe left action
- Right button = Swipe right action
- Same animations as swipe

### Support
- Touch (mobile) and mouse (desktop)
- Keyboard navigation for accessibility

---

## Data Structure

```javascript
// Transaction Object
{
  id: "txn_001",
  merchantName: "Standard Market Co",
  logoUrl: "/logos/standard-market.png",
  category: "Groceries",
  categoryIcon: "🛒",
  amount: 279.50,
  date: "Sep 10, 2025",
  isNecessary: null // null, true, or false
}

// Game State
{
  transactions: [],
  currentIndex: 0,
  timePeriod: "7 Days",
  completedTransactions: [],
  gameStarted: false,
  gameCompleted: false
}

// Results Data
{
  totalSavings: 439.00,
  unnecessaryCount: 8,
  necessaryCount: 17,
  powerMoves: [
    {
      id: 1,
      icon: "🔥",
      title: "Power Moves",
      description: "If you redirected $439/week you could"
    },
    {
      id: 2,
      icon: "✨",
      title: "Smash your car loan",
      description: "Save $10,014 on interest and finish your loan 1 year 4 months faster"
    },
    {
      id: 3,
      icon: "🚀",
      title: "Boost your home deposit",
      description: "Reach your goal in 1 year 5 months Vs 2 years 4 months"
    }
  ],
  unnecessaryTransactions: []
}
```

---

## Sample Transaction Data

```javascript
const transactions = [
  {
    id: 1,
    merchantName: "Standard Market Co",
    logoUrl: "standard_market_logo.png",
    category: "Groceries",
    categoryIcon: "🛒",
    amount: 279.50,
    date: "Sep 10, 2025"
  },
  {
    id: 2,
    merchantName: "Telstra",
    logoUrl: "telstra_logo.png",
    category: "Entertainment",
    categoryIcon: "📺",
    amount: 149.00,
    date: "Sep 11, 2025"
  },
  {
    id: 3,
    merchantName: "Greca Restaurant",
    logoUrl: "greca_logo.png",
    category: "Food & Drinks",
    categoryIcon: "🍽️",
    amount: 145.00,
    date: "Sep 13, 2025"
  },
  {
    id: 4,
    merchantName: "Zarraffa's Coffee",
    logoUrl: "zarraffas_logo.png",
    category: "Food & Drinks",
    categoryIcon: "☕",
    amount: 8.50,
    date: "Sep 16, 2025"
  },
  {
    id: 5,
    merchantName: "Uber Eats",
    logoUrl: "uber_eats_logo.png",
    category: "Food & Drinks",
    categoryIcon: "🍽️",
    amount: 48.50,
    date: "Sep 18, 2025"
  },
  {
    id: 6,
    merchantName: "Amazon",
    logoUrl: "amazon_logo.png",
    category: "Shopping",
    categoryIcon: "🛍️",
    amount: 97.99,
    date: "Sep 20, 2025"
  },
  {
    id: 7,
    merchantName: "Spotify",
    logoUrl: "spotify_logo.png",
    category: "Entertainment",
    categoryIcon: "🎵",
    amount: 14.99,
    date: "Sep 22, 2025"
  },
  {
    id: 8,
    merchantName: "Death Before Decaf",
    logoUrl: "death_before_decaf_logo.png",
    category: "Food & Drinks",
    categoryIcon: "☕",
    amount: 7.50,
    date: "Sep 24, 2025"
  },
  {
    id: 9,
    merchantName: "Function Well",
    logoUrl: "function_well_logo.png",
    category: "Health & Beauty",
    categoryIcon: "💪",
    amount: 99.95,
    date: "Sep 25, 2025"
  }
];
```

---

## Component Structure

```
/src
  /components
    - WelcomeScreen.jsx
    - TimePeriodSelector.jsx
    - TimePeriodModal.jsx
    - GameScreen.jsx
    - TransactionCard.jsx
    - ProgressIndicator.jsx
    - SwipeableCard.jsx
    - ActionButtons.jsx
    - ResultsScreen.jsx
    - SwipeScoreHeader.jsx
    - PowerMoveCard.jsx
    - TransactionListItem.jsx
  /hooks
    - useSwipe.js
    - useGameState.js
    - useModal.js
  /utils
    - transactionData.js
    - calculateResults.js
  /styles
```

---

## Design System

### Colors
- **Primary Background:** #1E3A5F (dark blue)
- **Card Background:** #FFFFFF (white)
- **Accent Orange:** #FF8C42
- **Power Move Icon Background:** #FF8C42 (orange square)
- **Button Blue:** #5DADE2
- **Button Red:** #E74C3C
- **Button Green:** #2ECC71
- **Score Card Red:** #E74C3C
- **Score Card Green:** #2ECC71
- **Text Dark:** #2C3E50
- **Text Light:** #7F8C8D

### Typography
- **Title:** 28-32px, Bold
- **Swipe Score Header:** 24-28px, Bold
- **Savings Amount:** 48-64px, Extra Bold (huge)
- **Score Card Number:** 32-40px, Bold
- **Score Card Label:** 14-16px, Bold, Uppercase
- **Power Move Title:** 16-18px, Bold
- **Power Move Description:** 14-16px, Regular
- **Section Header:** 18-20px, Bold
- **Merchant Name:** 18-20px, Regular
- **Amount:** 32-40px, Bold (on cards), 18-20px Bold (on list)
- **Category:** 14-16px, Regular
- **Date:** 12-14px, Light

### Spacing
- Card border-radius: 16px
- Button border-radius: 12px (circular for action buttons)
- Modal border-radius: 20px
- Card shadow: 0 4px 12px rgba(0,0,0,0.15)
- Modal backdrop: rgba(0,0,0,0.5)
- Standard padding: 16-24px

### Responsive Breakpoints
- Mobile: < 768px (primary)
- Tablet: 768px - 1024px
- Desktop: > 1024px

---

## Animations

### Card Animations
- **Entry:** Fade in + scale (0.95 → 1.0) in 300ms
- **Swipe Exit:** 
  - Left: translateX(-150%) + rotate(-15deg) in 400ms
  - Right: translateX(150%) + rotate(15deg) in 400ms
- **Drag:** Real-time transform based on touch/mouse position
- **Snap Back:** Spring animation in 200ms

### Progress Indicator
- Fill animation: Left to right in 300ms

### Button Feedback
- Press: Scale to 0.95 in 100ms
- Release: Scale to 1.0 in 100ms

### Modal Animations
- **Open:** Fade in backdrop + slide up modal from bottom (300ms)
- **Close:** Fade out backdrop + slide down modal (250ms)
- **Picker scroll:** Smooth momentum scrolling with snap-to-item

### Results Screen Animations
- **Screen entry:** Fade in with slight scale-up (400ms)
- **Savings amount:** Count-up animation from 0 to final amount (800ms)
- **Score cards:** Stagger slide-in from bottom (left card 200ms delay, right card 300ms delay)
- **Power Moves:** Fade in and slide up, staggered (100ms delay between each)
- **Transaction list:** Fade in after other elements (500ms delay)

---

## Technical Requirements

### Stack
- React 18+
- JavaScript or TypeScript (TypeScript recommended)
- CSS Modules / Styled Components / Tailwind CSS
- Framer Motion or React Spring (for animations)

### Performance
- 60fps smooth animations
- Touch/drag latency < 16ms
- Initial load < 2 seconds

### Browser Support
- Chrome, Safari, Firefox, Edge (modern versions)

### Accessibility
- Keyboard navigation
- ARIA labels
- Touch targets ≥ 44x44px
- Color contrast WCAG AA compliant
- Screen reader compatible

---

## Functional Requirements

### Welcome Screen
✓ Display game title and instructions  
✓ Show preview transaction card  
✓ Time period dropdown/button opens modal  
✓ Time Period Modal with scrollable picker  
✓ Modal SELECT button confirms choice and closes modal  
✓ Tap outside modal to close without selection  
✓ Start button validates selection and begins game  

### Game Screen
✓ Display current transaction card  
✓ Show progress indicator  
✓ Swipe left/right gesture detection  
✓ Button tap for left/right actions  
✓ Card exit animations on decision  
✓ Load next card from stack  
✓ Prevent accidental swipes (threshold)  
✓ Visual feedback during drag (tilt, opacity)  
✓ Show swipe direction indicators  
✓ Track all decisions  

### Results Screen
✓ Display "Your Swipe Score" header  
✓ Show total potential savings amount  
✓ Display count cards (unnecessary vs necessary)  
✓ Render "Power Moves" section with 3 insights  
✓ Each Power Move has icon, title, and description  
✓ Display "List of Unnecessary Spend" section  
✓ Show all unnecessary transactions in list format  
✓ Full screen scrollable content  
✓ Calculate savings based on user's categorizations  
✓ Optional: "Create Budget" or "Done" button at bottom  

---

## Edge Cases

- No transactions available → Show message
- Single transaction → Allow single swipe
- Long merchant names → Truncate with ellipsis
- Missing logos → Use placeholder icon
- Rapid swiping → Prevent animation queue buildup
- Network errors → Graceful error message with retry option

---

## Future Enhancements (Optional)

- Undo last decision
- Skip transaction
- Add notes to transactions
- Spending analytics dashboard
- Real banking API integration
- Custom categories
- Achievements/badges

---

**Document Version:** 1.0  
**Last Updated:** October 6, 2025
