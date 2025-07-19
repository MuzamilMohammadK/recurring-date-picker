# Recurring Date Picker Component

A modern, reusable React component for selecting recurring dates with advanced customization options. Built with Next.js, TypeScript, Tailwind CSS, and shadcn/ui components.

## 🚀 Features

### Core Functionality
- **Multiple Recurrence Types**: Daily, Weekly, Monthly, and Yearly
- **Customizable Intervals**: Every X days/weeks/months/years
- **Flexible Date Ranges**: Select start and optional end dates
- **Visual Calendar Preview**: Real-time display of recurring dates
- **Responsive Design**: Works seamlessly on desktop and mobile devices

### Advanced Customization
- **Weekly Patterns**: Select specific days of the week
- **Monthly Patterns**: Choose between date-based or weekday-based recurrence
- **Nth Weekday Selection**: "Second Tuesday of every month" patterns
- **Real-time Updates**: Instant preview of all recurring dates

### Technical Excellence
- **TypeScript**: Full type safety and IntelliSense support
- **Modular Architecture**: Clean, reusable component structure
- **State Management**: React Context API for efficient state handling
- **Testing**: Comprehensive unit and integration tests
- **Accessibility**: ARIA-compliant components and keyboard navigation

## 📦 Installation

```bash
# Clone the repository
git clone [repository-url]
cd recurring-date-picker

# Install dependencies
npm install

# Start development server
npm run dev
```

## 🎯 Usage

### Basic Implementation

```tsx
import { RecurringDatePicker } from '@/components/recurring-date-picker'
import { RecurringDateProvider } from '@/contexts/recurring-date-context'

function App() {
  return (
    <RecurringDateProvider>
      <RecurringDatePicker />
    </RecurringDateProvider>
  )
}
```

### Custom Integration

```tsx
import { useRecurringDate } from '@/contexts/recurring-date-context'

function CustomComponent() {
  const { state, dispatch, generatePreviewDates } = useRecurringDate()
  
  // Access current configuration
  console.log(state.recurrenceType) // 'daily' | 'weekly' | 'monthly' | 'yearly'
  console.log(state.interval) // 1-999
  console.log(state.startDate) // Date | null
  console.log(state.endDate) // Date | null
  
  // Generate preview dates
  generatePreviewDates()
  
  return (
    <div>
      <p>Next 5 occurrences:</p>
      {state.previewDates.slice(0, 5).map(date => (
        <div key={date.toISOString()}>
          {date.toLocaleDateString()}
        </div>
      ))}
    </div>
  )
}
```

## 🏗️ Architecture

### Component Structure
```
src/
├── components/
│   └── recurring-date-picker/
│       ├── recurring-date-picker.tsx      # Main component
│       ├── recurrence-options.tsx         # Recurrence type selection
│       ├── customization-features.tsx     # Advanced options
│       ├── date-range-selector.tsx        # Date picker
│       └── mini-calendar-preview.tsx      # Calendar view
├── contexts/
│   └── recurring-date-context.tsx         # State management
└── __tests__/
    ├── recurring-date-context.test.tsx    # Unit tests
    └── recurring-date-picker.integration.test.tsx  # Integration tests
```

### State Management
The component uses React Context API with a reducer pattern:

- **State**: Centralized state for all configuration options
- **Actions**: Type-safe actions for updating state
- **Preview Generation**: Automatic date calculation based on configuration

### Key Types
```typescript
type RecurrenceType = 'daily' | 'weekly' | 'monthly' | 'yearly'
type WeekDay = 'monday' | 'tuesday' | 'wednesday' | 'thursday' | 'friday' | 'saturday' | 'sunday'
type MonthlyPattern = 'date' | 'day'
```

## 🧪 Testing

### Run Tests
```bash
# Run all tests
npm test

# Run tests in watch mode
npm test -- --watch

# Run tests with coverage
npm test -- --coverage
```

### Test Coverage
- **Unit Tests**: Context state management and utility functions
- **Integration Tests**: Component interaction and user flows
- **Visual Tests**: Calendar rendering and date highlighting

## 🎨 Customization

### Styling
The component uses Tailwind CSS for styling. You can customize the appearance by:

1. **Theme Variables**: Modify Tailwind config
2. **Component Props**: Pass custom className props
3. **CSS Modules**: Override styles with CSS modules

### Configuration Options
- **Max Preview Dates**: Limit the number of preview dates (default: 50)
- **Date Format**: Customize date display format
- **Locale Support**: Internationalization ready

## 📱 Responsive Design

The component is fully responsive with:
- **Mobile-first**: Optimized for touch interactions
- **Tablet**: Enhanced spacing and layout
- **Desktop**: Full-featured experience with side-by-side layout

## 🔧 Development

### Prerequisites
- Node.js 18+
- npm or yarn

### Available Scripts
```bash
npm run dev          # Start development server
npm run build        # Build for production
npm run start        # Start production server
npm run lint         # Run ESLint
npm run test         # Run tests
```

### Project Structure
```
recurring-date-picker/
├── src/
│   ├── app/                 # Next.js app directory
│   ├── components/          # React components
│   ├── contexts/            # React contexts
│   ├── lib/                 # Utility functions
│   └── __tests__/           # Test files
├── public/                  # Static assets
├── jest.config.js          # Jest configuration
├── jest.setup.js           # Jest setup
└── package.json            # Dependencies and scripts
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- [shadcn/ui](https://ui.shadcn.com/) for the beautiful UI components
- [Radix UI](https://www.radix-ui.com/) for the accessible primitives
- [Tailwind CSS](https://tailwindcss.com/) for the utility-first styling
- [date-fns](https://date-fns.org/) for the date manipulation utilities
