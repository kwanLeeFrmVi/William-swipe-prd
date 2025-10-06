# Product Requirements Document: "Are You Spending Smart?" Swipe Game

## Overview

A Tinder-style swipe game for financial awareness. Users review past transactions and categorize them as "Necessary" or "Unnecessary" through an engaging swipe interface.

**Platform:** ReactJS web application (mobile-first, responsive)

---

## Visual Reference

Use the screenshots from the provided video to illustrate each screen and interaction state.

---

## User Flow

1. **Welcome Screen** → Select time period → Tap START
2. **Game Screen** → Swipe through transactions → Categorize each one
3. **Results Screen** → View all categorized transactions → Done

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

<img height="450" alt="image" src="https://github.com/user-attachments/assets/c3c1bd58-3802-4387-9dca-522cb1e99f9d" />


<img height="450" alt="image" src="https://github.com/user-attachments/assets/0709686c-a741-4e1a-8151-61681bf5a71f" />


**Action Buttons (Bottom):**
- **Left (Red #E74C3C):** Thumbs down icon, "Unnecessary" label
- **Right (Green #2ECC71):** Thumbs up icon, "Necessary" label

---

### 3. Results Screen

<img width="1080" height="1920" alt="image" src="https://github.com/user-attachments/assets/285af557-fae9-4423-873a-2db15a68a067" />

**Elements:**
- Scrollable list of all transactions
- Each item: Logo + Merchant Name + Category + Amount
- **Create Budget Button** (light blue)
- **DONE Button**

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
    - GameScreen.jsx
    - TransactionCard.jsx
    - ProgressIndicator.jsx
    - SwipeableCard.jsx
    - ActionButtons.jsx
    - ResultsScreen.jsx
    - TimePeriodSelector.jsx
  /hooks
    - useSwipe.js
    - useGameState.js
  /utils
    - transactionData.js
  /styles
```

---

## Design System

### Colors
- **Primary Background:** #1E3A5F (dark blue)
- **Card Background:** #FFFFFF (white)
- **Accent Orange:** #FF8C42
- **Button Blue:** #5DADE2
- **Button Red:** #E74C3C
- **Button Green:** #2ECC71
- **Text Dark:** #2C3E50
- **Text Light:** #7F8C8D

### Typography
- **Title:** 28-32px, Bold
- **Merchant Name:** 18-20px, Regular
- **Amount:** 32-40px, Bold
- **Category:** 14-16px, Regular
- **Date:** 12-14px, Light

### Spacing
- Card border-radius: 16px
- Button border-radius: 12px (circular for action buttons)
- Card shadow: 0 4px 12px rgba(0,0,0,0.15)
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
✓ Time period dropdown with options  
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
✓ Display all transactions in list  
✓ Show merchant info and amounts  
✓ "Create Budget" button (placeholder)  
✓ "Done" button returns to welcome screen  

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
