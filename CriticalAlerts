import SwiftUI

struct CriticalAlert: Identifiable {
    let id = UUID()
    let patientName: String
    let patientID: String
    let alertType: String
    let value: String
    let normalRange: String
    let timeAgo: String
    let active: Bool
}

let activeAlerts = [
    CriticalAlert(patientName: "Michael Chen", patientID: "P002", alertType: "Blood Pressure", value: "190/120 mmHg", normalRange: "120/80 mmHg", timeAgo: "2 minutes ago", active: true),
    CriticalAlert(patientName: "Maria Garcia", patientID: "P007", alertType: "Heart Rate", value: "135 BPM", normalRange: "60-100 BPM", timeAgo: "5 minutes ago", active: true),
    CriticalAlert(patientName: "Thomas Lee", patientID: "P010", alertType: "Oxygen Saturation", value: "88%", normalRange: "95-100%", timeAgo: "12 minutes ago", active: true)
]

let resolvedAlerts = [
    CriticalAlert(patientName: "Sarah Johnson", patientID: "P001", alertType: "Temperature", value: "103.2°F", normalRange: "98.6°F", timeAgo: "1 hour ago", active: false),
    CriticalAlert(patientName: "Emily Davis", patientID: "P003", alertType: "Blood Glucose", value: "45 mg/dL", normalRange: "70-140 mg/dL", timeAgo: "", active: false)
]

struct CriticalAlertsView: View {
    var body: some View {
        NavigationView {
            ScrollView {
                VStack(spacing: 16) {
                    // Header and Active Alert Count
                    HStack {
                        Text("Critical Alerts")
                            .foregroundColor(.white)
                            .font(.title)
                            .bold()
                        Spacer()
                        Text("3 Active")
                            .font(.subheadline)
                            .foregroundColor(.red)
                            .padding(.horizontal, 12)
                            .padding(.vertical, 4)
                            .background(Color.red.opacity(0.2))
                            .cornerRadius(15)
                    }
                    .padding(.horizontal)

                    // Banner
                    HStack {
                        Image(systemName: "exclamationmark.triangle.fill")
                            .foregroundColor(.yellow)
                        Text("3 critical alerts require immediate attention")
                            .foregroundColor(.white)
                            .font(.callout)
                        Spacer()
                    }
                    .padding()
                    .background(Color.red.opacity(0.3))
                    .cornerRadius(12)
                    .padding(.horizontal)

                    // Active Alerts
                    ForEach(activeAlerts) { alert in
                        AlertCard(alert: alert)
                            .padding(.horizontal)
                    }

                    // Resolved Alerts
                    ForEach(resolvedAlerts) { alert in
                        AlertCard(alert: alert)
                            .padding(.horizontal)
                    }

                    Spacer(minLength: 20)
                }
                .frame(maxWidth: .infinity)
                .padding(.vertical)
            }
            .background(Color.black.edgesIgnoringSafeArea(.all))
        }
        .navigationViewStyle(StackNavigationViewStyle())
    }
}

struct AlertCard: View {
    let alert: CriticalAlert

    var body: some View {
        VStack(alignment: .leading, spacing: 8) {
            HStack {
                Circle()
                    .fill(alert.active ? Color.red : Color.gray)
                    .frame(width: 12, height: 12)
                Text(alert.patientName)
                    .foregroundColor(alert.active ? .white : .gray)
                    .bold()
                Text("(\(alert.patientID))")
                    .foregroundColor(.gray)
                Spacer()
            }

            Text(alert.alertType)
                .foregroundColor(.gray)
            
            HStack {
                Text(alert.value)
                    .font(.title2)
                    .foregroundColor(alert.active ? .red : .gray)
                    .bold()
                Spacer()
                Text("Normal: \(alert.normalRange)")
                    .foregroundColor(.gray)
                    .font(.subheadline)
            }

            HStack {
                Image(systemName: "clock")
                    .foregroundColor(.gray)
                    .font(.caption)
                Text(alert.timeAgo)
                    .foregroundColor(.gray)
                    .font(.caption)
                Spacer()
            }

            HStack(spacing: 12) {
                Button(action: {}) {
                    HStack {
                        Image(systemName: "eye")
                        Text("View Patient")
                    }
                    .padding(.vertical, 8)
                    .padding(.horizontal)
                    .foregroundColor(alert.active ? Color.white : Color.gray)
                    .background(Color.black.opacity(0.8))
                    .cornerRadius(8)
                }
                if alert.active {
                    Button(action: {}) {
                        HStack {
                            Image(systemName: "checkmark.circle")
                            Text("Mark Resolved")
                        }
                        .padding(.vertical, 8)
                        .padding(.horizontal)
                        .foregroundColor(.white)
                        .background(Color.green)
                        .cornerRadius(8)
                    }
                } else {
                    HStack {
                        Image(systemName: "checkmark.circle")
                        Text("Resolved")
                    }
                    .padding(.vertical, 8)
                    .padding(.horizontal)
                    .foregroundColor(.green)
                    .background(Color.gray.opacity(0.3))
                    .cornerRadius(8)
                }
            }
        }
        .padding()
        .background(alert.active ? Color(red: 30/255, green: 35/255, blue: 40/255) : Color(red: 20/255, green: 20/255, blue: 23/255))
        .cornerRadius(16)
        .shadow(color: Color.black.opacity(0.3), radius: 4, x: 0, y: 2)
    }
}

// SwiftUI Preview
#Preview {
    CriticalAlertsView()
}

// If your Xcode doesn't support the #Preview macro, use instead:
// struct CriticalAlertsView_Previews: PreviewProvider {
//     static var previews: some View {
//         CriticalAlertsView()
//     }
// }

