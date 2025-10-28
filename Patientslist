import SwiftUI

struct PatientListScreen: View {
    @State private var selectedTab: Tab = .all
    @State private var searchText: String = ""
    @State private var patients: [Patient] = [
        Patient(id: "P001", name: "Sarah Johnson", age: 34, status: .normal),
        Patient(id: "P002", name: "Michael Chen", age: 67, status: .critical),
        Patient(id: "P003", name: "Emily Davis", age: 28, status: .normal),
        Patient(id: "P004", name: "Robert Wilson", age: 45, status: .normal),
        Patient(id: "P005", name: "Lisa Anderson", age: 52, status: .normal),
        Patient(id: "P006", name: "David Brown", age: 39, status: .normal),
        Patient(id: "P007", name: "Maria Garcia", age: 71, status: .critical)
    ]

    enum Tab: String, CaseIterable {
        case all = "All (12)"
        case critical = "Critical (3)"
        case stable = "Stable (9)"

        var color: Color {
            switch self {
            case .all: return Color(.systemTeal)
            case .critical: return Color(.systemRed)
            case .stable: return Color(.systemGreen)
            }
        }
    }

    var filteredPatients: [Patient] {
        let filtered = patients.filter { patient in
            searchText.isEmpty ||
            patient.name.localizedCaseInsensitiveContains(searchText) ||
            patient.id.localizedCaseInsensitiveContains(searchText)
        }
        switch selectedTab {
        case .all:
            return filtered
        case .critical:
            return filtered.filter { $0.status == .critical }
        case .stable:
            return filtered.filter { $0.status == .normal }
        }
    }

    var body: some View {
        NavigationView {
            ZStack {
                // Dark background for the screen
                Color(.black)
                    .edgesIgnoringSafeArea(.all)
                VStack(spacing: 0) {
                    // Search bar
                    HStack {
                        Image(systemName: "magnifyingglass").foregroundColor(.gray)
                        TextField("Search patients by name or ID...", text: $searchText)
                            .foregroundColor(.primary)
                    }
                    .padding(12)
                    .background(Color(.systemGray6))
                    .cornerRadius(12)
                    .padding(.horizontal, 16)
                    .padding(.top, 8)

                    // Tabs (Chips)
                    HStack {
                        ForEach(Tab.allCases, id: \.self) { tab in
                            Button(action: { selectedTab = tab }) {
                                Text(tab.rawValue)
                                    .font(.system(size: 14, weight: .semibold))
                                    .foregroundColor(selectedTab == tab ? .white : .primary)
                                    .padding(.vertical, 6)
                                    .padding(.horizontal, 16)
                                    .background(selectedTab == tab ? tab.color : Color(.systemGray5))
                                    .cornerRadius(16)
                            }
                        }
                        Spacer()
                    }
                    .padding(.horizontal, 16)
                    .padding(.vertical, 8)

                    ScrollView {
                        VStack(spacing: 12) {
                            ForEach(filteredPatients) { patient in
                                HStack(spacing: 16) {
                                    ZStack {
                                        Circle()
                                            .fill(Color(.systemGray5))
                                            .frame(width: 44, height: 44)
                                        Image(systemName: "person")
                                            .foregroundColor(.gray)
                                            .font(.system(size: 22))
                                    }
                                    VStack(alignment: .leading, spacing: 4) {
                                        Text(patient.name)
                                            .font(.system(size: 16, weight: .semibold))
                                            .foregroundColor(.black)
                                        HStack(spacing: 6) {
                                            Text("ID: \(patient.id)")
                                                .font(.system(size: 12))
                                                .foregroundColor(.gray)
                                            Text("·")
                                                .foregroundColor(.gray)
                                            Text("\(patient.age) years")
                                                .font(.system(size: 12))
                                                .foregroundColor(.gray)
                                        }
                                    }
                                    Spacer()
                                    if patient.status == .normal {
                                        Text("Normal")
                                            .font(.system(size: 13, weight: .medium))
                                            .foregroundColor(.green)
                                            .padding(.vertical, 4)
                                            .padding(.horizontal, 14)
                                            .background(
                                                Capsule().fill(Color.green.opacity(0.12))
                                            )
                                    } else {
                                        Text("Critical")
                                            .font(.system(size: 13, weight: .medium))
                                            .foregroundColor(.red)
                                            .padding(.vertical, 4)
                                            .padding(.horizontal, 14)
                                            .background(
                                                Capsule().fill(Color.red.opacity(0.13))
                                            )
                                    }
                                }
                                .padding(.horizontal, 12)
                                .padding(.vertical, 8)
                                .background(Color.white)
                                .cornerRadius(16)
                                .shadow(color: Color(.systemGray4).opacity(0.15), radius: 2, x: 0, y: 1)
                            }
                        }
                        .padding(.horizontal, 10)
                        .padding(.top, 8)
                    }
                    Text("Showing \(filteredPatients.count) of 12 patients")
                        .font(.system(size: 13))
                        .foregroundColor(.gray)
                        .padding(.vertical, 8)
                }
                .toolbarBackground(Color(.black), for: .navigationBar)
                .toolbarBackground(.visible, for: .navigationBar)
                .toolbarColorScheme(.dark, for: .navigationBar)
                .navigationBarTitle("Patient List", displayMode: .inline)
                .navigationBarItems(
                    leading: Button(action: {}) {
                        Image(systemName: "chevron.left").foregroundColor(.white)
                    },
                    trailing: Button(action: {}) {
                        Image(systemName: "plus")
                            .foregroundColor(.white)
                            .padding(8)
                            .background(Color(.systemTeal))
                            .clipShape(Circle())
                    }
                )
            }
        }
        .navigationViewStyle(StackNavigationViewStyle())
    }
}

struct Patient: Identifiable {
    let id: String
    let name: String
    let age: Int
    let status: Status

    enum Status {
        case normal, critical
    }
}

struct PatientListScreen_Previews: PreviewProvider {
    static var previews: some View {
        PatientListScreen()
    }
}

